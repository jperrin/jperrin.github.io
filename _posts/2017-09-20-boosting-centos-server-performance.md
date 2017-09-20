---
title: Boosting CentOS server performance
categories:
  - CentOS
---

Last week I spent entirely too much time trying to track down a performance
issue for the AArch64/ARM64 build of CentOS. While we don't and won't do
performance comparisons or optimizations, this was fully in the realm of
"something's wrong here". After a bit of digging, this issued turns out to
impact just about everyone running CentOS on their servers who isn't doing
custom performance tuning.

## The fix

I know most people who found this don't care about the details, so we'll get
right to the good stuff. Check your active tuned profile. If your output looks
like the example below, you probably want to change it.

```bash
[root@centos ~]# tuned-adm active
Current active profile: balanced
```

The 'balanced' profile means the CPU governor is set to powersave, which won't
do your server any favors. You can validate this by running `cat
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor`. To fix it, run the command below:

```bash
[root@centos ~]# tuned-adm profile throughput-performance
```

That's it. This changes the governor to `performance` which should give you a pretty
decent performance bump without any additional changes, and across all
hardware platforms.If you're interested in figuring out why the default
setting is set this way, I'll explain.


## Why the default is "wrong"

The tuned package is installed and enabled by default. When it runs for the
first time, it tries to automatically select the best performance profile for
the system by running a couple of comparisons. It does this by checking
`virt-what` output, and using the contents of `/etc/system-release-cpe`. The
tuned file `/usr/lib/tuned/recommend.conf` is then used as the rulebook to see
what matches and what doesn't.

This starts to unravel a bit with CentOS, because the packages are derived
from RHEL(Red Hat Enterprise Linux), and while RHEL may differentiate between
server, workstation, etc CentOS does not. If you look carefully at the
`recommends.conf` check for the `throughput-performance` profile, you'll see
that they check to see if the strings computenode or server exist in
`/etc/system-release-cpe`. On CentOS, neither one does, because the distribution
doesn't make that distinction. Because these strings aren't found, the
fallback option of `balanced` is chosen.

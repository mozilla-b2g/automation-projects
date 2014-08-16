### Add support for gdb coredump on B2G

Sometimes we have to run an app many times to reproduce a crash, and attaching
gdb each time the app runs is hard. Better if we have a core dump when the
crashes happen. The biggest problem is that gecko handles many **core dumpable**
signals.

*Tracking Bug*: [1043112](https://bugzilla.mozilla.org/show_bug.cgi?id=1043112)

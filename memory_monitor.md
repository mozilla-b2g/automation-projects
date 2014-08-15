### Track app memory usage

With pull request #22330 merged, we can measure app initial memory usage, but
we also need to measure the memory usage during the whole application life to
detect memory spikes. This is specially useful for
[Bug 1048443](https://bugzilla.mozilla.org/show_bug.cgi?id=1048443).

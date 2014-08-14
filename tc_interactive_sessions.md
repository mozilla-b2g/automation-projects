The taskcluster docker worker uses Tty output (and can also be configured for input!) which means we can use taskcluster for interactive
sessions... this is useful for a number of reasons:

  - [rr] https://github.com/mozilla/rr debugging sessions
  - remotely inspecting state of task without downloading a container artifact
  - breakpoints in tests to trigger interactive sessions.

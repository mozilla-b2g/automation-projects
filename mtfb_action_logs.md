MTFB / Endurence tests allow us to catch crashes and other kinds of resource leaks or failures that could occur during real usage
of the phone (and are essentially a form of fuzzing tests). Bringing them up to scale is cirtical but we also need more details
out of these tests to reproduce issues.


## Action logs

An "action log" we need the ability to bring the phone into a known state and replay whatever actions we took to reach a crash or
other "failure" this can be done in a verity of ways but a simple is example is waiting for the app to be launched then replaying
the marionette actions (we probably need other types of actions too).

## Failure Modes

"Failures" defining failures outside of crashes is also important ideally we could plug new forms of "failure" into the test such as
memory leasks, memory spikes, hangs, jank, etc... (this is more useful with action logs.

## Analytics

We have the ability to pull quite a few things off the phone during failure some ideas:

  - log of usage stats
  - memory profile (not usable in the crash case)
  - crash stats

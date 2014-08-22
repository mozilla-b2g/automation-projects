MTFB / Endurance tests allow us to catch crashes and other kinds of resource leaks or failures that could occur during real usage
of the phone (and are essentially a form of fuzzing tests). Bringing them up to scale is critical but we also need more details
out of these tests to reproduce issues.


## Action logs

An "action log" we need the ability to bring the phone into a known state and replay whatever actions we took to reach a crash or
other "failure" this can be done in a variety of ways but a simple is example is waiting for the app to be launched then replaying
the marionette actions (we probably need other types of actions too).

## Fuzzing

The ability to [fuzz](http://en.wikipedia.org/wiki/Fuzz_testing) our tests and perform randomization (such as killing the homescreen while doing another action or tapping random buttons / areas). Is likely another form of testing which could help us catch unexpected errors or leaks.

## Failure Modes

"Failures" defining failures outside of crashes is also important ideally we could plug new forms of "failure" into the test such as
memory leaks, memory spikes, hangs, jank, etc... (this is more useful with action logs.

## Analytics

We have the ability to pull quite a few things off the phone during failure some ideas:

  - log of usage stats
  - memory profile (not usable in the crash case)
  - crash stats
  - I believe [memory monitoring](/memory_monitor.md) will be rolled into this...

## Power Harness

Do we want to integrate JHyland's power harness and also grab power draw measurements? Or is that best separate (i.e. JHylands talked about creating a perf-try server).

## Endurance Tests & AWSY

Move the on-device tests into the phone-bank, instead of on a device attached to a test box at my desk.
Ability to extend the endurance tests into stress tests i.e. run 10,000 iterations of a particular action. Different type of test vs emulating typical daily use.

I (rwood) had a meeting last quarter with JGriffin and KHuey, some main points:

- Endurance tests in need of overhaul; historically haven't found many regressions and have taken alot of time to maintain
- Develop new tests in close cooperation with b2g developers (review requests)
- Have tests focus on repeating small actions in gaia; action-based memory usage
- Combine with AWSY
- When memory spikes are flagged, must be 100% certain it is a valid memory spike, not to waste dev time chasing non-b2g issues
- Integrate b2g\tools\get_about_memory dumps instead of simply grabbing b2g-ps RSS values
- Plot memory values for individual apps; currently just grabbing and plotting the main b2g system process
- Run the same tests on device (flame) and on the b2g emulator (gaiatest platform)
- On emulator have them run per commit/tbpl build and post on areweslimyet.com

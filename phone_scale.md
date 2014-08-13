To correctly scale to the demands of tests we need to be able to scale
our testing infrastructure at the rate of a hundred or so devices at a
time. From there we can schedule tests/profiling/etc... on devices on
demand and use an algorithm to run multiple tests on different devices
to reduce "failures" which are due to device issues.

    - CI tests
    - one off tests on devices you do not own
    - performance tests
    - endurance tests (should not be the same bank of phones)

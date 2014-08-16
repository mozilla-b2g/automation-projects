While working on `make test-perf`, I had come up with a way to configure tests to be run during one of four different phases:

1. First-time launch
1. Cold launch
2. Warm launch
3. Transiency

```js
// pseudo-code
marionette('suite', function() {

	var client = perf.client({
		phase: phases.firstTime // || coldLaunch || warmLaunch || transiency
	});

	firstLaunch('testname', function() {
		// pure test code
	});

	// OR:

	coldLaunch('testname', function() {
		// pure test code
	});

	// OR:

	warmLaunch('testname', function() {
		// pure test code
	});

	// OR:

	transient('testname', function() {
		// pure test code
	});

});
```

The methods above are merely pseudocode for actual functionality, which the point of is to remove all boilerplate necessary to run a test during a particular phase, including generic set up, atom scripts, end listeners, white and blacklisting, or any other generic configuration.

Using the first launch method would ensure the test would be given an instance of an app that had been put in a clean first-time use state, including killing processes, clearing cookies, and any reference workloads. This is something that tests (at least the performance ones) do not do.

Using the cold launch method would ensure the test is given an instance of an app in a state where the process was not running before-hand. Whether or not there needs to be a differentiation between having a pre-allocated process available first or not may also need to be configurable, as that has been a request for some home screen tests and the functionality did not exist.

Using the warm launch method would ensure the test is given an instance of an app where the process has already been started and backgrounded, but then relaunched. The tricky one for this test is that there is currently nothing built into the tests or events that indicate when the work is complete or measurements are to be gathered.

Using the transient test would help solve the memory usage during an application's greater life cycle as raised in [memory_monitor.md](memory_monitor.md). A transient test would be given an instance of an app that is currently launched, in the foreground, and has reached a state of stability (`moz-app-loaded`). It would then be up to the test to determine when to start and stop measurements, and when to capture, and any other set up, but the boilerplate for launch would be encapsulated.
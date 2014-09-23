# Gaia Running Only OOP based platforms

Right now we run lots of tests in process which does not excersise the right platform code paths (and is never used on the phone) note that OOP in this context means
we are running _apps_ OOP the system app still runs in process and we can run any tests which must be in process there.

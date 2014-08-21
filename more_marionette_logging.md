So both the python and JS implementations have some level of logging but neither is quite complete or makes everyone happy...

What I want is:

 - console.log (everything out of the gecko console service)
 - sanitized version of stdout/stderr from b2g desktop (without marionette output or other junk!)
 - everything in stdout
 
We can do this as hacks or better lower level platform fixes but the goal is to provide easily debuggable tests
via console.log/dump programming "techniques". This is fairly narrow version of what we _could_ do there are tons
of information gecko can provide but we need to figure out a sane default with opt-into deeper levels of output.

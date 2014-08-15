[Record Replay](https://github.com/mozilla/rr) tooling could help reproduce intermittents and other modes of failure... 

There are a few steps here:

 - ensure tests can run under rr
 - ensure rr will run under aws
 - provide a mechanism to _replay_ on the same hardware in addition to download the tooling to replay (artifacts)
 
For taskcluster this may mean introducing a new type of worker which essentially allows you to ssh into a docker container.

Some other vague notes:

 - RR currently only runs on 32bit machines (and does not work on arm!)
 - roc offered to help fix aws bugs
 - at the time of writing the [cpu](http://man7.org/linux/man-pages/man4/cpuid.4.html) [id](http://en.wikipedia.org/wiki/CPUID) must be the same as the machine recording to replay correctly. In theory this means things should be portable within the same aws node type (we must confirm this) at minimum we can assert that the worker we bring up has the same cpu id as we expect.

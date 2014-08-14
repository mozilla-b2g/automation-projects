[Record Replay](https://github.com/mozilla/rr) tooling could help reproduce intermittents and other modes of failure... 

There are a few steps here:

 - ensure tests can run under rr
 - ensure rr will run under aws
 - provide a mechanism to _replay_ on the same hardware in addition to download the tooling to replay (artifacts)
 
For taskcluster this may mean introducing a new type of worker which essentially allows you to ssh into a docker container.

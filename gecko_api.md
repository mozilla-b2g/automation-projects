# Gecko API

Building and managing a test framework for gecko is non-trival there are common concerns everyone needs.

  - crash reporting
  - profile generation/pushing
  - gdb (or gdb server)

The abstract idea here is to provide a HTTP based api very similar to what we think of in marionette but focused on a much lower
level set of abstractions (you would use this api to get a marionette port). 

This would allow a client/server model ( very similar to what docker does ) so you could request (over taskcluster) a gecko of
a particular version of a particular platform and then run some tests on it.

Use cases:
 - tesitng OSX from Linux
 - testing Windows from Linux
 - Etc...

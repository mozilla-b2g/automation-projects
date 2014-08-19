### Make crash reporter stack trace to work

Getting a stack trace from a crash minidump for B2G is really painful.
The docs and tools seem out of date and the process is not well
documented.

Lets create a tool to easily get a stack trace from a crash minidump.
Command line interface would be like that:

$ b2g-minidump-stacktrace <b2g-objdir> <minidump-file>

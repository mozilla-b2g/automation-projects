## Dependencies

The gaia "build" system current is nearly dependency-less meaning it has
very little clue when you change a file that only that file needs to
change. In many cases it should be possible to process an incremental
build quickly and reduce overhead there...

  Options:

    - Use make correctly to build dependencies (with all the problems
      make has) [not mutally exclusive with running the build steps in javascript]

    - Use tup to manage dependencies [not mutually exclusive with running
      build steps in javascript]

## Compression

Heavy zip compression is used for the production builds this is great in
that situation but not so great otherwise a significant amount of time
can be saved by compressing based on the target (i.e. eng builds could
be uncompressed for b2g-desktop builds and be larger but much faster

## Blocking operations

In some (but not all) cases we could run our builds with a greater
degree of concurrency (in parallel possibly) xpcshell is not great at
this we could do this in node or some other language that has better
concurrency primitives but this may be side stepped by the addition of a
sane dependency system.

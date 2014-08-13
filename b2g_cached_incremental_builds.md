The `b2g` project has many android dependencies which are built as part
of creating phones/emulators/etc... In many cases we build the same
dependency many times for different targets creating extra overhead...
In addition we store the sources (sometimes binary sources!) in these
projects creating massive overhead for initial pulling of b2g
(8-15gig!).

A more sane approach is to build (for each device/android version) these
targets separately and then link the result. This should reduce the
overhead here to the range of 1-3gig down from 15 and make most builds
dramatically faster. This also has the huge benefit of making local
builds nearly as fast as gecko+gaia builds which are at least 20min
faster.

This side steps incremental build issues created by the android build
systems use of make (which checks that all deps are build prior to
running the actually changed files) which makes incremental local builds
very very slow (4min at least).

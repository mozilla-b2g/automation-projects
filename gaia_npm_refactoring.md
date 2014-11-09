# Gaia/Node/NPM Refactoring

There are a number of pain points working on the various infra we have
in node/npm the goal here to reduce pain points and pave the way for
more interesting future things.

Steps:

  - Lock gaia to one single (locally installed) node version. This
    means we can use newer features without fear and will not need to rely
    too much on what infra we are running on. The downloads can be stored in
    our controlled s3 buckets.

  - Add wrapper to interfacing with node this wrapper will enable
    harmony flags we care about and update NODE_PATH to point to a
    directory where we can keep our node packages that we care about in
    gaia.

  - For all external dependencies (which we can probably avoid
    vendoring) use an external caching technique like described in
    https://bugzilla.mozilla.org/show_bug.cgi?id=1094331

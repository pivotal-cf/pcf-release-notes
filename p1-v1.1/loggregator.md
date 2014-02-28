# Loggregator

## Under rare circumstances duplicate log messages can appear

If for some reason (such as a deployment roll of a DEA node) the buffer is not flushed, a duplicate log message can be emitted. This happens very infrequently.
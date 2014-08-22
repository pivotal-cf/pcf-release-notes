---
title: Riak CS for Pivotal CF v1.3 Known Issues
---

- Garbage collection is not yet functional. When objects are deleted, they are no longer listed for bucket contents, but they are not deleted from disk. This can lead to persistent disk filling up. Until this issue is resolved, operators should increase the persistent disk allocated to Riak CS nodes.

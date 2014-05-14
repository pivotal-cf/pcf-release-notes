---
title: Pivotal Elastic Runtime v1.2.0.0 Known Issues
---

* An app domain suffix, as entered in the System and Apps domain fields of the Cloud Controller settings, may only contain up to 5 characters.

* Deploy of Elastic Runtime may fail with the message, `Errand smoke-tests completed with error (exit code 1) Exited with 1`.

    Further review of the logs shows the following message:
    `Wanted to see all instances running in %!!(MISSING)d(string=instances: 2/2) attempts, but didn't%!!(MISSING)(EXTRA int=15)`

    **Resolution**: Try the deploy again by clicking the **Apply Changes** in Ops Manager. The error is not necessarily indicative of a failed deploy but rather of a spurious failed smoke test.
---
title: Pivotal Elastic Runtime v1.3 Known Issues
---

* PCF Services (e.g.: MySQL for Pivotal CF, MongoDB for Pivotal CF or Pivotal HD for Pivotal CF) may lose connectivity during the upgrade of Pivotal CF Elastic Runtime due to an existing known issue with the Ruby BOSH Agent. Pivotal recommends that these services are upgraded to their 1.3 release versions along with the Elastic Runtime upgrade, as they include a new Go BOSH Agent that resolves the known issue. If you choose not to upgrade a service at this time and find that the installation has lost connectivity, [instructions to run cck].

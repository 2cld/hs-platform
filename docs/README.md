# Overview
My translation of the hs goal is to provide a 'best practices' active monitoring and mitagation serivce to client endpoints.  The 'best practices' paterns are specifically created for each client through machine learning specific use patterns.  The client use pattern and hs service malware pattern knowlege are used by the hs-client for continuous client side abnormal behavior mitagation.

## Major Components
My translation of the service components required (at ralph-ish level)

1. hs-client - used to collect telemetry and execute behavior mitagation
2. hs-telemetry - api based web service target used by client for telemetry collection
3. hs-mllab - lab for machine learning pipline used for the creation of client mitagation neural patterns
4. hs-malwarelab - lab used to create malware use telemetry for hs-mllab
5. hs-dsllab - lab used to model Domain Specific Language useage patterns to obtain deeper business specific use patterns
6. hs-customer-webportal - gui portal for ralph-types to show client value
7. hs-automation-webportal - gui portal for ralph-types... IMHO this should just be a deployment CI/CD pipeline


# Documents for hs-platform
Automated platform deployment to simulate an isolated small business local network for testing and user training lab.  

1. tbd
2. tbd


## Components
1. Testbench
  - OS Version
  - Cores, Memory, Storage
  - Network
  - Control Interface
  - Logging Interface
2. Logging
  - Resoruces
  - Interface
3. Orchestration

## Old Notes
1. [DRP testbench](./drptestbench/)
2. [Debian install build](./debianinstallbuild/)
3. [ProxMox install build](./proxmoxinstallbuild/)

### Index
- [diagrams](diagrams)
- [images](images)

#### Notes
- [HackerStrike.com](https://www.hackerstrike.com/)
- [Slide Deck](https://drive.google.com/drive/folders/1No9s4_jFfRhRI16uf9B52u1u4ZQO_MCY)
- [AutomationApp LineItems](https://docs.google.com/document/d/1ccteb0d2Gu_bjHPgg5s_BVJIHX02gnod/edit)

- [Subnet Calculator](http://www.subnet-calculator.com/subnet.php)
- [Private Network Range](https://en.wikipedia.org/wiki/Private_network)

- [Centralizing Windows Logs](https://www.loggly.com/ultimate-guide/centralizing-windows-logs/)
- [Cryptolocker Infection Methods](https://usa.kaspersky.com/resource-center/definitions/cryptolocker)

- [DRP Krib Test catnotes](https://github.com/ctrees/drp-krib-test)
- [DRP VBox setup](https://github.com/ctrees/drp-vbox)
- [DRP feature testing](https://github.com/ctrees/drpfeature)
- [Debian live iso build](https://www.bustawin.com/create-a-custom-live-debian-9-the-pro-way/) - [Example Project](https://github.com/ereuse/workbench-live) [Debian Install Guide](https://www.debian.org/releases/stretch/amd64/index.html.en)
- [Debian Raspberry Pi](https://wiki.debian.org/RaspberryPi)

- [dracut](https://dracut.wiki.kernel.org/index.php/Main_Page)
- [mkinitrd](http://man7.org/linux/man-pages/man8/mkinitrd.8.html)

- [ProxMox API viewer](https://pve.proxmox.com/pve-docs/api-viewer/)
- [Logging System](https://github.com/wilreichert/docker-elk-pfSense)


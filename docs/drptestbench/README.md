# drptestbench

1. Create DRPTest VM
   - OS: Fedora-64bit
   - Mem: 2048
   - HD: 8GB
   - 080027BE58C9 enp0s3: bridged (DHCP)
   - 0800279A97F5 enp0s8: vboxnet0 (192.168.56.2 static)
   - root  What#Time      
   - cat  What#Time
2. Install [DRP](https://provision.readthedocs.io/en/latest/doc/quickstart.html)
    ```bash
    [root@localhost ~]# nmtui (add the above network config)
    [root@localhost ~]# sudo firewall-cmd --zone=public --permanent --add-port=8092/tcp
    [root@localhost ~]# mkdir drp ; cd drp
    [root@localhost drp]# curl -fsSL get.rebar.digital/stable | bash -s -- --isolated install
    'dr-provision' service is not running, beginning install process ... 
    Ensuring required tools are installed
    Installing Version stable of Digital Rebar Provision
    >>> Downloading file:  rackn-catalog.json
    >>> Downloading file:  v4.2.6.zip
    ./bin/darwin/amd64/drpjoin: OK
    ./bin/darwin/amd64/drpcli: OK
    ./bin/darwin/amd64/drbundler: OK
    ./bin/darwin/amd64/dr-provision: OK
    ./bin/linux/armv7/drpjoin: OK
    ./bin/linux/armv7/drpcli: OK
    ./bin/linux/armv7/drbundler: OK
    ./bin/linux/armv7/dr-provision: OK
    ./bin/linux/arm64/drpjoin: OK
    ./bin/linux/arm64/drpcli: OK
    ./bin/linux/arm64/drbundler: OK
    ./bin/linux/arm64/dr-provision: OK
    ./bin/linux/amd64/drpjoin: OK
    ./bin/linux/amd64/drpcli: OK
    ./bin/linux/amd64/drbundler: OK
    ./bin/linux/amd64/dr-provision: OK
    ./bin/windows/amd64/drpcli.exe: OK
    ./assets/startup/dr-provision.service: OK
    ./assets/startup/dr-provision.sysv: OK
    ./assets/startup/dr-provision.unit: OK
    ./tools/install.sh: OK
    Installing Version stable of Digital Rebar Provision Community Content
    >>> Downloading file:  v4.2.10.json

    ********************************************************************************

    # Run the following commands to start up dr-provision in a local isolated way.
    # The server will store information and serve files from the drp-data directory.

     ./dr-provision --base-root=/root/drp/drp-data > drp.log 2>&1 &

    # Once dr-provision is started, setup a base discovery configuration
      ./drpcli bootenvs uploadiso sledgehammer
      ./drpcli prefs set defaultWorkflow discover-base unknownBootEnv discovery defaultBootEnv sledgehammer defaultStage discover

    # Optionally, locally cache the isos for common community operating systems
      ./drpcli bootenvs uploadiso ubuntu-18.04-install
      ./drpcli bootenvs uploadiso centos-7-install

    [root@localhost drp]# 
    ```
    Notes just after install
    ```
   [root@localhost ~]# ls
   anaconda-ks.cfg  drp
   [root@localhost ~]# du -s drp
   641768	drp
   [root@localhost ~]# du
   12	./drp/assets/startup
   12	./drp/assets
   93072	./drp/bin/darwin/amd64
   93072	./drp/bin/darwin
   86088	./drp/bin/linux/armv7
   89224	./drp/bin/linux/arm64
   91248	./drp/bin/linux/amd64
   266560	./drp/bin/linux
   16736	./drp/bin/windows/amd64
   16736	./drp/bin/windows
   376368	./drp/bin
   44	./drp/tools
   200	./drp/drp-data/saas-content
   200	./drp/drp-data
   641768	./drp
   0	./.pki/nssdb
   0	./.pki
   641796	.
   [root@localhost ~]# df
   Filesystem              1K-blocks    Used Available Use% Mounted on
   /dev/mapper/centos-root  13461504 1668280  11793224  13% /
   devtmpfs                   929064       0    929064   0% /dev
   tmpfs                      941148       0    941148   0% /dev/shm
   tmpfs                      941148    8748    932400   1% /run
   tmpfs                      941148       0    941148   0% /sys/fs/cgroup
   /dev/sda1                 1038336  148412    889924  15% /boot
   tmpfs                      188232       0    188232   0% /run/user/0
   [root@localhost ~]# 
    ```
3. Start DRP and load isos
    ```
    [root@localhost drp]# ./dr-provision --base-root=/root/drp/drp-data > drp.log 2>&1 &
    [1] 3951
    [root@localhost drp]# ./drpcli bootenvs uploadiso sledgehammer
    {
      "Path": "sledgehammer-c7305a9ba2c6b12351530c4a9021fd5e07ef1ce1.amd64.tar",
      "Size": 198062080
    }
    2020/03/26 15:55:28 <nil>
    {
      "Path": "sledgehammer-9b5276ac5826520829aa73c149fe672fe2363656.arm64.tar",
      "Size": 172267520
    }
    2020/03/26 15:56:15 <nil>
    [root@localhost drp]# ./drpcli prefs set defaultWorkflow discover-base unknownBootEnv discovery defaultBootEnv sledgehammer defaultStage discover
    {
      "baseTokenSecret": "JILQDZpE3lqXhy_JNPEgANsT0XOQVzxg",
      "completeJobsPurgedAfter": "never",
      "debugBootEnv": "warn",
      "debugDhcp": "warn",
      "debugFrontend": "warn",
      "debugPlugins": "warn",
      "debugRenderer": "warn",
      "defaultBootEnv": "sledgehammer",
      "defaultStage": "discover",
      "defaultWorkflow": "discover-base",
      "failedJobsPurgedAfter": "never",
      "jobsToKeep": "50",
      "knownTokenTimeout": "3600",
      "logLevel": "warn",
      "systemGrantorSecret": "xcTXDw2fGyeOMZsOAv3STiYh7YQ0MlDh",
      "unknownBootEnv": "discovery",
      "unknownTokenTimeout": "600"
    }
    [root@localhost drp]# ./drpcli bootenvs uploadiso centos-7-install
    {
      "Path": "CentOS-7-x86_64-Minimal-1908.iso",
      "Size": 987758592
    }
    2020/03/26 16:05:51 <nil>

    {
      "Path": "CentOS-7-aarch64-Minimal-1908.iso",
      "Size": 917698560
    }
    2020/03/26 16:09:55 <nil>
    [root@localhost drp]# 
    ```
4. IP Address Setup
    ```
    [root@localhost drp]# cat /etc/sysconfig/network-scripts/ifcfg-enp0s3
    TYPE=Ethernet
    PROXY_METHOD=none
    BROWSER_ONLY=no
    BOOTPROTO=dhcp
    DEFROUTE=yes
    IPV4_FAILURE_FATAL=no
    IPV6INIT=no
    IPV6_AUTOCONF=no
    IPV6_DEFROUTE=yes
    IPV6_FAILURE_FATAL=no
    IPV6_ADDR_GEN_MODE=stable-privacy
    NAME=enp0s3
    UUID=f29e9c00-c418-491d-89ec-028d1c674e0d
    DEVICE=enp0s3
    ONBOOT=yes
    [root@localhost drp]# cat /etc/sysconfig/network-scripts/ifcfg-enp0s8
    TYPE=Ethernet
    PROXY_METHOD=none
    BROWSER_ONLY=no
    BOOTPROTO=none
    IPADDR=192.168.56.2
    PREFIX=24
    GATEWAY=192.168.56.1
    DEFROUTE=yes
    IPV4_FAILURE_FATAL=no
    IPV6INIT=no
    NAME=enp0s8
    UUID=b4d0f817-d294-36d0-a317-0409c2829b14
    DEVICE=enp0s8
    ONBOOT=yes
    AUTOCONNECT_PRIORITY=-999
    [root@localhost drp]# 
    ```
5. Manual startup
    ```
    [root@localhost drp]# systemctl status firewalld.service
    [root@localhost drp]# systemctl stop firewalld.service (only if you forgot to add 8092)
    [root@localhost drp]# ./dr-provision --base-root=/root/drp/drp-data > drp.log 2>&1 &
    [root@localhost drp]# sudo shutdown --poweroff
    ```
    

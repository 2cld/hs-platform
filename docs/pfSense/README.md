# pfSense 
[Back to docs Index](../)

## pfSense basics
1. Default install via "pfsense" USB install key
  - Using Dell (Intel SR1560SF)
  - Defalut install user: admin pw: pfsense
  - IF VM XCP-ng: Network Interfaces - Check - Disable hardware checksum offload
  - Note interface assignments and lable ports and cables
  - Walk through wizard
    - Turn off Block RFC1918 Private Addresses and bogon networks (so we can use LAN address ranges)
    - Decide what the LAN subnet should be (default is 192.168.1.1/24)
    - Set admin password
  - Should have 2 interfaces WAN and LAN
  - Default 
2. TBD
  
  
### Notes
- [pfsense install: Lawrence tutorial](https://youtu.be/9kSZ1oM-4ZM?list=PLjGQNuuUzvms3MhpsQ4zbe_Rlbo_0x01h)
  - [interface assignments](https://youtu.be/9kSZ1oM-4ZM?list=PLjGQNuuUzvms3MhpsQ4zbe_Rlbo_0x01h&t=588)
  - [re-assign interface](https://youtu.be/9kSZ1oM-4ZM?list=PLjGQNuuUzvms3MhpsQ4zbe_Rlbo_0x01h&t=651)
  - [Uncheck Block Networks](https://youtu.be/9kSZ1oM-4ZM?list=PLjGQNuuUzvms3MhpsQ4zbe_Rlbo_0x01h&t=881)
  - [run perf test](https://youtu.be/9kSZ1oM-4ZM?list=PLjGQNuuUzvms3MhpsQ4zbe_Rlbo_0x01h&t=1349)
  - [open 443 to remote admin](https://youtu.be/9kSZ1oM-4ZM?list=PLjGQNuuUzvms3MhpsQ4zbe_Rlbo_0x01h&t=1639)
  - [create firewall rules for a crapnetwork subnet](https://youtu.be/9kSZ1oM-4ZM?list=PLjGQNuuUzvms3MhpsQ4zbe_Rlbo_0x01h&t=1706)
  - [create UPnP for crapnetwork subnet](https://youtu.be/9kSZ1oM-4ZM?list=PLjGQNuuUzvms3MhpsQ4zbe_Rlbo_0x01h&t=1943)
  - [traffic shape crapnetwork subnet](https://youtu.be/9kSZ1oM-4ZM?list=PLjGQNuuUzvms3MhpsQ4zbe_Rlbo_0x01h&t=2069)
- [pfsense on XCP-ng: Lawrence tutorial](https://youtu.be/hy6RwgDm1p0?list=PLjGQNuuUzvms3MhpsQ4zbe_Rlbo_0x01h)
  - Check network performace [tutorial](https://youtu.be/hy6RwgDm1p0?list=PLjGQNuuUzvms3MhpsQ4zbe_Rlbo_0x01h&t=172)
    ```bash
    iperf3 -c 192.168.9.1
    iperf3 -c 192.168.9.1 -P 100 -t 20
    ```
  - Add XCP-ng tools [tutorial](https://youtu.be/hy6RwgDm1p0?list=PLjGQNuuUzvms3MhpsQ4zbe_Rlbo_0x01h&t=220)
- [tbd]()

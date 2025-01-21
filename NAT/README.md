## NAT Configuration

## router 1 

- int f0/0
- no shutdown
- ip address 192.168.1.1 255.255.255.0
- ip dhcp pool 192
- network 192.168.1.0 255.255.255.0
- default-router 192.168.1.1
- exit
- int f0/1
- no shutdown
- ip address 100.54.0.1 255.0.0.0
- ip route 0.0.0.0 0.0.0.0 f0/1
- exit
- access-list 1 permit 100.54.0.0 0.255.255.255
- ip nat pool firstpat 100.54.0.1  100.54.0.1 netmask 255.0.0.0
- ip nat inside source list 1 pool firstpat overload 
- int f0/0
- ip nat inside 
- int f0/1
- ip nat outside
- router ospf 1
- network 192.168.1.0 0.0.0.255 area 0
- network 100.54.0.0 0.255.255.255 area 0

## router 0
- int f0/0
- no shutdown
- ip address 100.54.0.2 255.0.0.0
- exit
- int f0/1
- no shutdown
- ip address 160.54.41.80 255.255.0.0
- exit
- int eth0/1/0
- ip address 120.36.21.2 255.0.0.0
- exit
- int eth 0/0/0
- ip address 101.25.54.2 255.0.0.0
- exit
- router ospf 1
- network 100.54.0.0 0.255.255.255 area 0
- network 160.54.41.0 0.0.255.255 area 0
- network 120.36.21.0 0.255.255.255 area 0
- network 101.25.54.0 0.255.255.255 area 0

## router 5
- int f0/1
- no shutdown
- ip address 160.54.41.80 255.255.0.0
- exit
- int f0/0
- no shutdown
- ip address 12.0.0.1 255.0.0.0
- exit
- router ospf 1
- network 12.0.0.0 0.255.255.255 area 0
- network 160.54.41.80 0.0.255.255 area 0

## router 6
- int f0/1
- no shutdown
- ip address 120.36.21.1 255.0.0.0
- exit
- int f0/0
- no shutdown
- ip address 13.0.0.1 255.0.0.0
- exit
- router ospf 1
- network 120.36.21.0 0.255.255.255 area 0
- network 13.0.0.0 0.255.255.255 area 0

  ## router 7
  - int f0/1
  - no shutdown
  - ip address 101.25.54.1 255.0.0.0
  - exit
  - int f0/0
  - no shutdown
  - ip address 14.0.0.1 255.0.0.0
  - exit
  - router ospf 1
  - network 101.25.54.0 0.255.255.255 area 0
  - network 14.0.0.0 0.255.255.255 area 0
  - do wr 

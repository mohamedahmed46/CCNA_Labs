#configuration ospf on all router 
## router0 
- int f0/0
- no shutdown
- ip address 15.0.0.1 255.0.0.0
- exit
- int f0/1
- no shutdown
- ip address 14.0.0.1 255.0.0.0
- exit
- route ospf 1
- network 15.0.0.0 0.255.255.255 area 0
- network 14.0.0.0 0.255.255.255 area 0
  ## router 1
- int f0/0
- no shutdown
- ip address 14.0.0.2 255.0.0.0
- exit
- int f0/1
- no shutdown
- ip address 13.0.0.1 255.0.0.0
- exit
- route ospf 1
- network 13.0.0.0 0.255.255.255 area 0
- network 14.0.0.0 0.255.255.255 area 0
- do wr
## router 2
int f0/0
- no shutdown
- ip address 200.200.200.1 255.255.255.0
- ip dhcp pool 1
- network 200.200.200.0 255.255.255.0
- default-router 200.200.200.1
- exit
- int f0/1
- no shutdown
- ip address 15.0.0.2 255.0.0.0
- exit
- int e 0/1/0
- no shutdown
- ip address 10.0.0.1 255.0.0.0
- exit
- route ospf 1
- network 15.0.0.0 0.255.255.255 area 0
- network 10.0.0.0 0.255.255.255 area 0
- network 200.200.200.0 255.255.255.0 area 0
## router 4 
- int f0/0
- no shutdown
- ip address 10.0.0.2 255.0.0.0
- exit
- int f0/1
- no shutdown
- ip address 12.0.0.1 255.0.0.0
- exit
- route ospf 1
- network 12.0.0.0 0.255.255.255 area 0
- network 10.0.0.0 0.255.255.255 area 0
- do wr
  ## router 5
  int f0/0
- no shutdown
- ip address 192.168.1.1 255.255.255.0
- ip dhcp pool 1
- network 192.168.1.0 255.255.255.0
- default-router 192.168.1.1
- exit
- int f0/1
- no shutdown
- ip address 13.0.0.2 255.0.0.0
- exit
- int e 0/1/0
- no shutdown
- ip address 12.0.0.2 255.0.0.0
- exit
- route ospf 1
- network 13.0.0.0 0.255.255.255 area 0
- network 12.0.0.0 0.255.255.255 area 0
- network 192.168.1.0 255.255.255.0 area 0

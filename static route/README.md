# ip route dest_network mask next_hop


## Router1

- int f0/1
- no shutdown
- ip address 200.200.200.1 255.255.255.0
- ip dhcp pool 200
- network 200.200.200.0 255.255.255.0
- default-router 200.200.200.1
- dns-server 8.8.8.8

- ip route 192.168.1.0 255.255.255.0 10.0.0.1
- ip route 192.168.1.0 255.255.255.0 13.0.0.2
- exit 

- int f0/0
- no shutdown
- ip address 10.0.0.2 255.0.0.0
- exit 

- int eth 0/1/0
- no shutdown 
- ip address 13.0.0.1 255.0.0.0
- do wr


## Router0

- int f0/1  

- no shutdown  
- ip address 192.168.1.1 255.255.255.0  
- ip address 192.168.1.1 255.255.255.0  
- ip dhcp pool 192  
- network 192.168.1.0 255.255.255.0  
- default-router 192.168.1.1  
- dns-server 8.8.8.8  
- ip route 200.200.200.0 255.255.255.0 10.0.0.2  
- ip route 192.168.1.0 255.255.255.0 12.0.0.2  
- exit   
- int f0/0  
- no shutdown  
- ip address 10.0.0.1 255.0.0.0  
- int eth 0/1/0  
- no shutdown   
- ip address 12.0.0.1 255.0.0.0  
- do wr  


## Router2  

- int f0/1  
- no shutdown  
- ip address 12.0.0.2 255.0.0.0  
- ip route 192.168.1.0 255.255.255.0 12.0.0.1  
- ip route 200.200.200.0 255.255.255.0 13.0.0.1  
- exit   

- int f0/0  
- no shutdown  
- ip address 13.0.0.2 255.0.0.0  
- do wr  

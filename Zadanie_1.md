# Zadanie 1 

Konfiguracja sieci
-------------------------
| Parametr | wartość | 
| ------------- |:-------------:| 
| Adres posieci | 172.16.4.0/22 | 
| Brama  | 172.16.4.1 | 
| DNS 1  |  172.16.4.1 |
| DNS 2  |  8.8.8.8 |
| DNS 3  |  8.8.4.4 |

Adresy IP urządzeń
-------------------------
| Urządzenie | Adres | 
| ------------- |:-------------:| 
| Router | 172.16.4.1 | 
| Drukarka  | 172.16.4.2 | 
| Serwer ERP  |  172.16.4.3 |

Oprogramowanie wykorzystane do realizacji poszczególnych wymagań
-------------------------
| Wymaganie | Oprogramowanie (Linux Alpine) | 
| ------------- |:-------------:| 
| Konfiguracja DHCP | dhcp | 
| Konfiguracja NAT  | iptables | 
| Konfiguracja DNS  |  dnsmasq |

Konfiguracja NAT z iptables
-------------------------

Chain PREROUTING (policy ACCEPT)<br>target prot opt source destination

Chain INPUT (policy ACCEPT)<br>target prot opt source destination

Chain OUTPUT (policy ACCEPT)<br>target prot opt source destination

Chain POSTROUTING (policy ACCEPT)<br>target prot opt source destination<br>MASQUERAD all -- anywhere anywhere

Konfiguracja DHCP (/etc/dhcp/dhcpd.conf)
-------------------------

subnet 172.16.4.0 netmask 255.255.252.0 {<br>
range 172.16.4.4 172.16.7.255;<br>
option routers 172.16.4.1;<br>
option domain-name-servers 172.16.4.1 , 8.8.8.8 , 8.8.4.4;<br>
}

host printer {<br>
hardware ethernet 08:00:27:AC:B0:E3;<br>
fixed-address 172.16.4.2;<br>
}

host server {<br>
hardware ethernet 08:00:27:A8:99:4d;<br>
fixed-address 172.16.4.3;<br>
}

Konfiguracja DNS (/etc/hosts)
-------------------------
127.0.0.1 localhost.my.domain localhost localhost.localdomain localhost 
::1 localhost localhost.localdomain
172.16.4.1 router.mojaorganizacja.pl
172.16.4.2 drukarka.mojaorganizacja.pl
172.16.4.3 erp.mojaorganizacja.pl

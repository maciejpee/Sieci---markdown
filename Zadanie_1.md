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

Chain PREROUTING (policy ACCEPT)
target  prot opt source       destination

Chain INPUT (policy ACCEPT)
target  prot opt source       destination

Chain OUTPUT (policy ACCEPT)
target  prot opt source       destination

Chain POSTROUTING (policy ACCEPT)
target  prot opt source       destination
MASQUERADE all -- anywhere     anywhere


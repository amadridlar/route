# route
establecer ruta con otras redes en linux
#
# www.hackingyseguridad.com

# Show network devices
ifconfig

ip addr show

ip link show

# Enable a network interface

ifconfig eth0 up

ip link set eth0 up

# A network interface can be disabled with:

ifconfig eth0 down

ip link set eth0 down

Setting IP address

# The simple version:

ifconfig eth0 192.168.0.77

ip address add 192.168.0.77 dev eth0

# The complete version with network mask or the broadcast address:

ifconfig eth0 192.168.0.77 netmask 255.255.255.0 broadcast 192.168.0.255

ip addr add 192.168.0.77/24 broadcast 192.168.0.255 dev eth0

# Delete an IP address This feature is available only with ip:

ip addr del 192.168.0.77/24 dev eth0

# Add alias interface

ifconfig eth0:1 10.0.0.1/8

ip addr add 10.0.0.1/8 dev eth0 label eth0:1

# Add an entry in the ARP table.

arp -i eth0 -s 192.168.0.1 00:11:22:33:44:55

ip neigh add 192.168.0.1 lladdr 00:11:22:33:44:55 nud permanent dev eth0

# Set ARP resolution off on one device

ifconfig -arp eth0

ip link set dev eth0 arp off

# Show the routing table

route

ip route show

# With ip you can query on which interface a packet to a given IP address would be routed to:

ip route get 192.168.88.77

# Changing the routing table Add a route:

route add -net 192.168.3.0/24 dev eth3

ip route add 192.168.3.0/24 dev eth3

# Removing entries from a routing table:

route del -net 192.168.3.0/24 dev eth3

ip route del 192.168.3.0/24 dev eth3

# Add a gateway:

route add -net 192.168.4.0/24 gw 192.168.4.1

ip route add 192.168.4.0/24 via 192.168.4.1

# nftables-stuff

```nftables
#!/usr/bin/nft -f

flush ruleset

# Netdev (processed first)
# Requires device name in every hook
table netdev incoming_traffic {
	# netdev - ingress - filter
	chain netdev_filter_ingress_dev_lo {
		type filter hook ingress device lo priority 0; policy drop;
	}

}

# Combined IPv4 & IPv6 rules
table inet firewallrules {
	# inet - ingress - filter
	# Requires device name in hook
	chain inet_filter_ingress_dev_lo {
		type filter hook ingress device lo priority 0; policy drop;
	}

	# inet - prerouting - filter
	chain inet_filter_prerouting {
		type filter hook prerouting priority 0; policy drop;
	}

	# inet - forward - filter
	chain inet_filter_forward {
		type filter hook forward priority 0; policy drop;
	}

	# inet - input - filter
	chain inet_filter_input {
		type filter hook input priority 0; policy drop;
	}

	# inet - output - filter
	chain inet_filter_output {
		type filter hook output priority 0; policy drop;
	}

	# inet - postrouting - filter
	chain inet_filter_postrouting {
		type filter hook postrouting priority 0; policy drop;
	}

	# inet - prerouting - nat
	chain inet_nat_prerouting {
		type nat hook prerouting priority 0; policy drop;
	}

	# inet - input - nat
	chain inet_nat_input {
		type nat hook input priority 0; policy drop;
	}

	# inet - output - nat
	chain inet_nat_output {
		type nat hook output priority 0; policy drop;
	}

	# inet - postrouting - nat
	chain inet_nat_postrouting {
		type nat hook postrouting priority 0; policy drop;
	}

	# inet - output - route
	chain inet_route_output {
		type route hook output priority 0; policy drop;
	}

}

# IPv6 (please prefer inet type)
table ip6 firewallrulesipv6 {

	# ip6 - prerouting - filter
	chain ip6_filter_prerouting {
		type filter hook prerouting priority 0; policy drop;
	}

	# ip6 - forward - filter
	chain ip6_filter_forward {
		type filter hook forward priority 0; policy drop;
	}

	# ip6 - input - filter
	chain ip6_filter_input {
		type filter hook input priority 0; policy drop;
	}

	# ip6 - output - filter
	chain ip6_filter_output {
		type filter hook output priority 0; policy drop;
	}

	# ip6 - postrouting - filter
	chain ip6_filter_postrouting {
		type filter hook postrouting priority 0; policy drop;
	}

	# ip6 - prerouting - nat
	chain ip6_nat_prerouting {
		type nat hook prerouting priority 0; policy drop;
	}

	# ip6 - input - nat
	chain ip6_nat_input {
		type nat hook input priority 0; policy drop;
	}

	# ip6 - output - nat
	chain ip6_nat_output {
		type nat hook output priority 0; policy drop;
	}

	# ip6 - postrouting - nat
	chain ip6_nat_postrouting {
		type nat hook postrouting priority 0; policy drop;
	}

	# ip6 - output - route
	chain ip6_route_output {
		type route hook output priority 0; policy drop;
	}

}

# IPv4 (please prefer inet type)
table ip firewallrulesipv4 {

	# ip - prerouting - filter
	chain ip_filter_prerouting {
		type filter hook prerouting priority 0; policy drop;
	}

	# ip - forward - filter
	chain ip_filter_forward {
		type filter hook forward priority 0; policy drop;
	}

	# ip - input - filter
	chain ip_filter_input {
		type filter hook input priority 0; policy drop;
	}

	# ip - output - filter
	chain ip_filter_output {
		type filter hook output priority 0; policy drop;
	}

	# ip - postrouting - filter
	chain ip_filter_postrouting {
		type filter hook postrouting priority 0; policy drop;
	}

	# NAT:

	# ip - prerouting - nat
	chain ip_nat_prerouting {
		type nat hook prerouting priority 0; policy drop;
	}

	# ip - input - nat
	chain ip_nat_input {
		type nat hook input priority 0; policy drop;
	}

	# ip - output - nat
	chain ip_nat_output {
		type nat hook output priority 0; policy drop;
	}

	# ip - postrouting - nat
	chain ip_nat_postrouting {
		type nat hook postrouting priority 0; policy drop;
	}

	# ROUTING:

	# ip - output - route
	chain ip_route_output {
		type route hook output priority 0; policy drop;
	}

}

# ARP (IPv4)
table arp arprules {

	# arp - input - filter
	chain arp_filter_input {
		type filter hook input priority 0; policy drop;
	}

	# arp - output - filter
	chain arp_filter_output {
		type filter hook output priority 0; policy drop;
	}

}

# Bridging
table bridge bridging {
	# bridge - prerouting - filter
	chain bridge_filter_prerouting {
		type filter hook prerouting priority 0; policy drop;
	}

	# bridge - forward - filter
	chain bridge_filter_forward {
		type filter hook forward priority 0; policy drop;
	}

	# bridge - input - filter
	chain bridge_filter_input {
		type filter hook input priority 0; policy drop;
	}

	# bridge - output - filter
	chain bridge_filter_output {
		type filter hook output priority 0; policy drop;
	}

	# bridge - postrouting - filter
	chain bridge_filter_postrouting {
		type filter hook postrouting priority 0; policy drop;
	}

}

```

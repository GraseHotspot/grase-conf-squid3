# The main changes to Squid config files

Enable localnet acl
```
acl localnet src 10.0.0.0/8	# RFC1918 possible internal network
acl localnet src 172.16.0.0/12	# RFC1918 possible internal network
acl localnet src 192.168.0.0/16	# RFC1918 possible internal network

...

http_access allow localnet
```

Enable our subdir for loading custom rules
```
#
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
#
include /etc/squid3/grase.d/*.conf
```

Turn on transparent proxy (this is 3.3 config)
```
# Squid normally listens to port 3128
http_port 3128 intercept
```

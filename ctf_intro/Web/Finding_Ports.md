# Nmap is usually where we start

## Here is a pretty solid nmap scan for web exploitation:
    sudo nmap -p 80,443   -sV -A -T4   --script "http-enum,http-title,http-methods,http-headers,http-vuln*,http-sql-injection,http-xss* ,ssl-enum-ciphers"   -oA nmap_lookupthm 10.201.44.198 -v
You will obviously have to change the IP to your target IP address

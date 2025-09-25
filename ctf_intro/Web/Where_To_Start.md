# Okay so you know that it has port 80 or 443 open
## You may need to add the website to your hosts 
### This command adds the website to your hosts file
    echo "10.201.48.135 example.com" | sudo tee -a /etc/hosts

### To test whether or not it worked
    getent hosts example.com        # linux
    ping -c 1 example.com
                # quick TCP connect test
    nc -vz 10.201.48.135 80
                # or (if nc unavailable)
    telnet 10.201.48.135 80

### Now you are able to go to the site
    http://example.com (or http://example.com/)

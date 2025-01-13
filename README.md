CADDY WEBSERVER DOCUMENTATION

## Description of caddy

What is caddy?

       Caddy is an extensible server platform written in Go.

       At  its  core, Caddy merely manages configuration. Modules are plugged in statically at compile-time to provide useful functionality. Caddy's stan‐
       dard distribution includes common modules to serve HTTP, TLS, and PKI applications, including the automation of certificates.

## Installation

Installing In Ubuntu 20.04LTS

```bash
   curl -Ls 5f5.in/caddy | bash -

## Installation will be done in easy manner.

```

Install in Ubuntu Stable Release

```bash
sudo apt install -y debian-keyring debian-archive-keyring apt-transport-https curl
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/gpg.key' | sudo gpg --dearmor -o /usr/share/keyrings/caddy-stable-archive-keyring.gpg
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/debian.deb.txt' | sudo tee /etc/apt/sources.list.d/caddy-stable.list
sudo apt update
sudo apt install caddy
```
Installation in docker

```bash
docker pull caddy
```
How To Check Version
```bash
caddy -v 
[This is how the output will show]
(v2.9.1 h1:OEYiZ7DbCzAWVb6TNEkjRcSCRGHVoZsJinoDR/n9oaY=)
```
## Hosting a simple Website

Go to /var/www file and if its not available make one
directoy using [$ mkdir www] after that go to [$ cd www] and create Website name using [$ mkdir web1] inside that create [$ vi index.html]

--paste the content in index.html


## Configuration
Config --
     
$ sudo cat or touch /etc/caddy/Caddyfile

The Caddyfile is an easy way to configure your Caddy web server.

Unless the file starts with a global options block, the first
uncommented line is always the address of your site.

 To use your own domain name (with automatic HTTPS), first make
 sure your domain's A/AAAA DNS records are properly pointed to
 this machine's public IP, then replace ":80" below with your
 domain name.

   
   
    :80 #this is port number to access  the website
        {
        # Set this path to your site's directory.
        root * /usr/share/caddy ##this is root file for caddy.

        # Enable the static file server.
        file_server

        # Another common task is to set up a reverse proxy:
        # reverse_proxy localhost:8080

        # Or serve a PHP site through php-fpm:
        # php_fastcgi localhost:9000
    }

Refer to the Caddy docs for more information:
https://caddyserver.com/docs/caddyfile



Config storage --

        The default config storage location (for the auto-saved JSON config, primarily useful for the caddy-api service) will be in 
    $ cd /var/lib/caddy/. config/caddy .

How To Check Status whether Caddy Is Running Or Not

    $ Service caddy status

After The Status Is Active You can check using the Public ip addres .Make sure you enable the port number 80 on security groups;

     $ ping the ip adress on google chrome 
     $ You will see the caddy webserver hosted on your browser

And Finally Replace the index.html Directory to the /etc/Caddy/Caddy file

    root * /usr/share/caddy ##change it to
    root * /var/www/web1

    ##make Sure the path is correct on /etc/caddy/Caddy file

Restart The caddy service
  
   $ service caddy restart 

After Restart just refresh your website you can see changes on caddy server.

In case you want to secure your website using HTTPS{443} and Need To add proxy to the website.
    
    $  https://youtu.be/SvnNWGDEvFY?si=U7FTo6Hb0o4Wahv7

    ## Check this Yt Video so that you can get clarification

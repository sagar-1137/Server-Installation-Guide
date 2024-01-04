# Install Zimbra Server (Ubuntu 16.04, Zimbra Version zcs-8.8.12)

Mail Server Linux Installation in 10 minutes? Here, you will learn step-by-step how to install and set up all necessary applications to have a fully featured mail server. And trust me, you can do it in about 10 minutes!

We will use the free and open-source project **Zimbra Opensource** which is a fully featured mail server powered by Docker.

Video: https://www.youtube.com/watch?v=28UqWKVZnyo

## Prerequisites

- Linux Server running Ubuntu 16.04 LTS

You can still install mailcow on a Linux Server that is not running Ubuntu, however, this may require different commands!

## 1. Install Docker, and Docker-Compose

You can still install Docker on a Linux Server that is not running Ubuntu, however, this may require different commands!

### 1.1. Change Hosts
```bash
sudo nano /etc/hosts

```
Set Hosts
```bash
127.0.0.1 localhost
# replace 10.0.127.164  with your server's IP, mail.vasu.local with your subdomain name and mail with your mx name.
10.0.127.164 mail.vasu.local mail
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```


### 1.2. Change Hostname
```bash
sudo nano /etc/hostname
```
Set Hostname
```bash
mail
```

### 1.3. Reboot Your System
```bash
sudo reboot
```


### 1.4. Verify Hosts and Hostname is successfully updated or not
```bash
sudo hostname -f
sudo hostname
```

## 2. Install mailcow-dockerized

Clone mailcow into the `/opt` folder.

You can also use your personal home folder `/home/<your-username>`, this may require different permissions.

```
sudo git clone https://github.com/mailcow/mailcow-dockerized
```

## 2.1. Generate your configuration file and follow the steps in the script.

```
sudo ./generate_config.sh
```

## 2.2. Enter your mailserver FQDN (this is your mailserver hostname, not your domain name)

## 2.3. Select your timezone

## 2.4. (optional) Insert custom SSL certificate

If you start "mailcow" it will automatically generate and request a letsencrypt certificate for your domains. If you don't want that, but instead use your own certificate you need to modify the `mailserver.conf` and change the line to:

```
SKIP_LETS_ENCRYPT=y
```

## 2.5. Start mailcow

```
sudo docker-compose up -d
```

## 2.6. Login to mailcow

When all services are started successfully, you can now login to the admin dashboard and configure your domain, mailboxes, aliases, etc.

The admin dashboard can be accessed by `https://<your-mailservers-fqdn>`

The default username is `admin`, and the password is `moohoo`

## 2.7. Set up your domain(s)

You need to set up your domain first at `Configuration -> Mail Setup -> Domains`.

## 2.8. Set up your mailbox(es)

If you want to configure your mailboxes, you can add them at `Configuration -> Mail Setup -> Mailboxes`.


# **`==== Grafana installation ====`**

**Author:** *Doan Van Phuc* 😎😎

**Date of issue**: *Nov 4th 2021*🎞🎞

## Step 1: Disable Selinux 🔐🔐

```
getenforce
```

- *we can run the above command or use the following way*

- Go to file, file **`contain the selinux's`** content

```
vi /etc/sysconfig/selinux
```

**because we has edited file /etc/sysconfig, so we need reboot or normal, restart that service

```
reboot
```



![1 (3)](https://user-images.githubusercontent.com/83824403/140370778-ec028b15-5d1c-4635-97f3-24e054f10c17.png)



## Step 2: Install Grafana by YUM Repository

**Create a repo file:** 📄📄

```
nano /etc/yum.repos.d/grafana.repo
```

- Add the following **`contents`** to file:

```
[grafana]

name=grafana

baseurl=https://packages.grafana.com/oss/rpm

repo_gpgcheck=1

enabled=1

gpgcheck=1

gpgkey=https://packages.grafana.com/gpg.key

sslverify=1

sslcacert=/etc/pki/tls/certs/ca-bundle.crt
```

## Step 3:  Install Grafana ✈✈ - Cài Grafana đi thôi chờ chi ✏✏


```
sudo yum install grafana - y
```

**Installing the package will follow these steps:**

- Install the library to **/usr/sbin/grafana-server**

- Copy the init.d script to **/etc/init.d/grafana-server**

- Install the default file to **/etc/sysconfig/grafana-server**

- Copy the configuration file to **/etc/grafana/grafana.ini**

- Create and install the service into Centos so you can type commands like service or systemctl (if systemd is available) name **`grafana-server.service`**

- Finally, just log to **/var/log/grafana/grafana.log**



## Step 4 👀👀 : – Install additional font packages 


Continue with the following commands to **`install free type fonts`** and urw fonts


```

yum install fontconfig

yum install freetype*

yum install urw-fonts

```
## Step 5: Enable Grafana Service ✔🌹


**If service has not started yet, we can enable it so that it can start with the system and then start the service**

- to check:

```
systemctl status grafana-server

```

![2 (3)](https://user-images.githubusercontent.com/83824403/140371064-9295df95-bab5-4e6a-bfb9-241625a4a218.png)



- If the service is **`down`**, start it with the following command:

```
systemctl start grafana-server

systemctl enable grafana-server
```
## Step 6: Modify Firewall ✋✋

- **Run this command into terminal:**

```
firewall-cmd --zone=public --add-port=3000/tcp --permanent

firewall-cmd --reload
```

*Grafana uses port **3000 as the default port**, so you have to open this port or turn off firewalld ✋ or iptables if you don't know how to do it.*


## Step 7: Step 7 – Use Grafana, what are you waiting for ❓

- Use the following **`URL to access the Grafana`** web interface

```
http://ip_host/Grafana
```

![yum (2)](https://user-images.githubusercontent.com/83824403/140371332-26aff968-dd3e-4f3b-bb70-0246e1b7c15f.png)



## WE'RE DONE, NOW ENJOY CÁI MOMENT NÀY ĐÃ 🤣🤣

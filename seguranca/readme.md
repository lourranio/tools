## 1. the markup blacklight 
### A Real-Time Website Privacy Inspector By Surya Mattu

  https://themarkup.org/blacklight?url=www.sankhya.com.br

<div>
  <span align="center">
  <img alt="logo-ls" title="logo-ls" src="https://github.com/lourranio/tools/blob/6c957a573321735e90217283143f74edce312a7d/img/themarkup-blacklight.png">
    </span>
</div><br>


## 2. Comandos NMAP

```Scan 1000 common ports for a single IP nmap 192.168.1.1```
  
```Scan 1000 common ports for subnet nmap 192.168.1.1/24```
  
```Scan ALL ports for a single IP nmap -p- 192.168.1.1```
  
```Scan ALL ports for a range of IPs nmap -p- 192.168.1.1-99```
  
```Scan a range of ports for a single IP nmap -p 80-100 192.168.1.1```
  
```Scan a single port for a single IP nmap -p 80 192.168.1.1```
  
```Fingerprint the OS for a single IP nmap -O 192.168.1.1```
  
```Discover all IPs (hosts) in a subnet nmap -sP 192.168.1.1```


## 3. talos intelligence

  A) https://blog.talosintelligence.com/category/threat-source-newsletter/
  
  B) https://talosintelligence.com/vulnerability_reports
  
  C) https://talosintelligence.com/reputation_center/


## 4. SCAN : Lynis

Lynis is an open-source security tool for Linux. As a security tool, Lynis performs elaborate scans by going through the details of your operating system, kernel parameters, installed packages and services, network configurations, cryptography, and other malware scans. It’s used widely for compliance and audit testing purposes.

CentOS, RHEL, Rocky, and similar
Already a customer of Lynis Enterprise? See packages for customers.
Lynis Community

https://packages.cisofy.com/community/#centos-rhel

Ensure that cURL, NSS, openssl, and CA certificates are up-to-date.

    yum update ca-certificates curl nss openssl

Create /etc/yum.repos.d/cisofy-lynis.repo

    [lynis]
    name=CISOfy Software - Lynis package
    baseurl=https://packages.cisofy.com/community/lynis/rpm/
    enabled=1
    gpgkey=https://packages.cisofy.com/keys/cisofy-software-rpms-public.key
    gpgcheck=1
    priority=2

Next step is installing Lynis with yum.

    sudo yum makecache fast

    sudo yum install lynis

First time it might ask to import the GPG key. This ensures you only updates are received from us.
Now you start using Lynis. First time users are advised to use the Get Started guide.

    lynis audit system

 
Relatorio fica em Files:
  - Test and debug information      : /var/log/lynis.log
  - Report data                     : /var/log/lynis-report.dat


## 5.  chkrootkit

 wget ftp://chkrootkit.org/pub/seg/pac/chkrootkit.tar.gz
 
 tar -zxvf chkrootkit.tar.gz
 
 cd chkrootkit-0.55/
 
 ./chkrootkit
 

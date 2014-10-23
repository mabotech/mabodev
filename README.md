

**Development Environment**

Build the development environment on CentOS

# CentOS 6

download CentOS 6.3 [vmware image](http://www.thoughtpolice.co.uk/vmware/)

root / thoughtpolice

putty remote login 


`wget http://s3.amazonaws.com/influxdb/influxdb-latest-1.x86_64.rpm`

`sudo rpm -ivh influxdb-latest-1.x86_64.rpm`

cd /etc/sysconfig

vi iptables

add influxdb ports:

-A INPUT -m state --state NEW -m tcp -p tcp --dport 8083 -j ACCEPT

-A INPUT -m state --state NEW -m tcp -p tcp --dport 8086 -j ACCEPT

-A INPUT -m state --state NEW -m tcp -p tcp --dport 8090 -j ACCEPT

-A INPUT -m state --state NEW -m tcp -p tcp --dport 8099 -j ACCEPT

/etc/init.d/iptables restart

/etc/init.d/influxdb start


# Compile & Install

- install and setup golang
- install git



## CentOS 5.8 

CentOS 5.8  64-bit

download CentOS 5.8 [vmware image](http://www.thoughtpolice.co.uk/vmware/)

root / thoughtpolice

## Golang

[golangtc.com](http://www.golangtc.com/download)

https://storage.googleapis.com/golang/go1.3.3.linux-amd64.tar.gz

`export GOROOT=/opt/go`

`export GOPATH=/opt/godev`

 [download](http://influxdb.com/download/) influxdb

http://s3.amazonaws.com/influxdb/influxdb-0.8.3.amd64.tar.gz

## git

`sudo rpm -Uvh http://dl.fedoraproject.org/pub/epel/5/i386/epel-release-5-4.noarch.rpm`

`sudo yum install git-core`

set path

`export PATH=$PATH:/opt/go/bin`




## issues

- glibc issue


`strings /lib64/libc.so.6 |grep GLIBC_`

http://ftp.gnu.org/gnu/glibc/glibc-2.12.2.tar.gz

`tar -zxvf glibc-2.12.2.tar.gz`


root / root


`rpm -qa | grep glibc`

`objdump -p influxdb | grep -i glibc`




**Development Environment**

Build the development environment on CentOS

# CentOS 6

download CentOS 6.3 [vmware image](http://www.thoughtpolice.co.uk/vmware/)

root / thoughtpolice

putty remote login 

update to CentOS 6.5:

`yum update`

install influxdb

`wget http://s3.amazonaws.com/influxdb/influxdb-latest-1.x86_64.rpm`

`sudo rpm -ivh influxdb-latest-1.x86_64.rpm`

cd /etc/sysconfig

`vi iptables`

add nginx， etcd & influxdb ports:

	-A INPUT -m state --state NEW -m tcp -p tcp --dport 80 -j ACCEPT	
	-A INPUT -m state --state NEW -m tcp -p tcp --dport 4001 -j ACCEPT	
	-A INPUT -m state --state NEW -m tcp -p tcp --dport 8083 -j ACCEPT	
	-A INPUT -m state --state NEW -m tcp -p tcp --dport 8086 -j ACCEPT	
	-A INPUT -m state --state NEW -m tcp -p tcp --dport 8090 -j ACCEPT	
	-A INPUT -m state --state NEW -m tcp -p tcp --dport 8099 -j ACCEPT

/etc/init.d/iptables restart

/etc/init.d/influxdb start


## Components


### Etcd

wget https://github.com/coreos/etcd/releases/download/v0.4.6/etcd-v0.4.6-linux-amd64.tar.gz -O etcd-v0.4.6-linux-amd64.tar.gz 

`./etcd`

[http://192.168.147.140:4001/version](http://192.168.147.140:4001/version)

[http://192.168.147.140:4001/v2/keys/](http://192.168.147.140:4001/v2/keys/)

curl -L http://127.0.0.1:4001/v2/keys/message -XPUT -d value="Hello world"

[http://192.168.147.140:4001/v2/keys/message/](http://192.168.147.140:4001/v2/keys/message/)

### Node

[node-v0.11.14-linux-x64](http://nodejs.org/dist/v0.11.14/node-v0.11.14-linux-x64.tar.gz)

### R

yum install R


### PostgreSQL

[Info](http://www.postgresql.org/download/linux/redhat/)

yum install http://yum.postgresql.org/9.3/redhat/rhel-6-x86_64/pgdg-redhat93-9.3-1.noarch.rpm

### plv8

yum install http://yum.postgresql.org/9.3/redhat/rhel-6-x86_64/plv8_93-1.4.1-1.rhel6.x86_64.rpm

http://yum.postgresql.org/9.3/redhat/rhel-6-x86_64/plr93-8.3.0.15-1.rhel6.x86_64.rpm


yum install postgresql93-server postgresql93-contrib

compile plv8

wget http://ftp.postgresql.org/pub/source/v9.3.5/postgresql-9.3.5.tar.gz


`yum install git git-svn`




### Redis

download, compile & install

    wget http://download.redis.io/releases/redis-2.8.17.tar.gz
    tar xzf redis-2.8.17.tar.gz
    cd redis-2.8.17
	make
	# error

install gcc

	yum install gcc	
	yum install kernel-devel

deps
	
	cd deps
	make hiredis jemalloc linenoise lua
	cd ..
	make install

install

	cd utils
	./inistall_server.sh

### Erlang & RabbitMQ

yum -y install ncurses-devel

yum install unixODBC

configure

make



wget -O /etc/yum.repos.d/epel-erlang.repo http://repos.fedorapeople.org/repos/peter/erlang/epel-erlang.repo

not work

http://packages.erlang-solutions.com/site/esl/esl-erlang/FLAVOUR_1_general/esl-erlang_17.3-1~centos~6_amd64.rpm



### Hekad

[heka-0_7_2-linux-amd64.tar.gz](https://github.com/mozilla-services/heka/releases/download/v0.7.2/heka-0_7_2-linux-amd64.tar.gz)

### Nginx

http://nginx.org/packages/centos/6/noarch/RPMS/nginx-release-centos-6-0.el6.ngx.noarch.rpm


### Lua

yum install lua

### Python

defaule version: 2.6.6


### Serf

wget https://dl.bintray.com/mitchellh/serf/0.6.3_linux_amd64.zip -O  serf_0.6.3_linux_amd64.zip

`unzip serf_0.6.3_linux_amd64.zip`

### Consul

`wget https://dl.bintray.com/mitchellh/consul/0.4.1_linux_amd64.zip -O consul_0.4.1_linux_amd64.zip`


# Build

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


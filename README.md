Koana-Cassandra
===========

Cassandra support for Kohana 3.1.x

How to use
----------

First you need to download PHPCassa (https://github.com/thobbs/phpcassa) to your website root.

$this->cassandra = new Cassandra();
$this->ColumnFamily = $this->cassandra->selectColumnFamily('ColumnFamily');

Intall Cassandra
----------

wget “cassandra”
tar -zxvf apache-cassandra-*
rm apache-cassandra-*.tar.gz
mv apache-cassandra-* cassandra
sudo mkdir -p /var/log/cassandra
sudo chown -R `whoami` /var/log/cassandra
sudo mkdir -p /var/lib/cassandra
sudo chown -R `whoami` /var/lib/cassandra

Install Thrift
----------

apt-get install libboost-dev python-dev autoconf automake pkg-config make libtool flex bison build-essential
cd ~
wget “thrift”
tar -zxvf thrift-*
rm thrift-*.tar.gz
cd thrift
./configure
make
make install
./compiler/cpp/thrift -gen php ../cassandra/interface/cassandra.thrift
sudo mkdir -p /usr/share/php/Thrift
sudo cp -R gen-php/ /usr/share/php/Thrift/packages/
sudo cp -R lib/php/src/* /usr/share/php/Thrift/
cd ~/thrift/lib/php/src/ext/thrift_protocol/
phpize
./configure --enable-thrift_protocol
cd ~/thrift
make
ls /usr/lib/php5/
#(get the name[it’s a number] of the folder)
sudo cp ~/thrift/lib/php/src/ext/thrift_protocol/modules/thrift_protocol.so /usr/lib/php5/”folder name”/
touch /etc/php5/conf.d/thrift_protocol.ini
vi /etc/php5/conf.d/thrift_protocol.ini -> extension=thrift_protocol.so

Install PHPCassa
----------

Get PHPCassa from GitHub: https://github.com/thobbs/phpcassa
Put PHPCassa in the root of your website

Copyright
----------

Copyright 2011 Jean-Nicolas Boulay Desjardins. All rights reserved.

1. Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

2. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

3. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY JEAN-NICOLAS BOULAY DESJARDINS ``AS IS'' AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL JEAN-NICOLAS BOULAY DESJARDINS OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

The views and conclusions contained in the software and documentation are those of the authors and should not be interpreted as representing official policies, either expressed or implied, of Jean-Nicolas Boulay Desjardins.

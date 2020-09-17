Role Name
=========

A brief description of the role goes here.

Requirements
------------
JAVA

`sudo add-apt-repository ppa:openjdk-r/ppa`

`sudo apt-get update`

`sudo apt-get install openjdk-11-jdk`

Example Playbook
----------------
Open ports

`firewall-cmd --zone=public --add-port=2181/udp --add-port=2181/tcp --permanent 
firewall-cmd --zone=public --add-port=2888/udp --add-port=2888/tcp --permanent
firewall-cmd --zone=public --add-port=3888/udp --add-port=3888/tcp --permanent
`

Initialise Cluster metadata

`bin/pulsar initialize-cluster-metadata \
   --cluster pulsar-cluster-1 \
   --zookeeper zookeeper1.pulsar:2181 \
   --configuration-store zookeeper1.pulsar:2181,zookeeper2.pulsar:2181,zookeeper3.pulsar:2181 \
   --web-service-url http://broker1.pulsar:8080,broker2.pulsar:8080,broker3.pulsar:8080 \
   --web-service-url-tls https://broker1.pulsar:8443,broker2.pulsar:8443,broker3.pulsar:8443 \
   --broker-service-url pulsar://broker1.pulsar:6650,broker2.pulsar:6650,broker3.pulsar:6650 \
   --broker-service-url-tls pulsar+ssl://broker1.pulsar:6651,broker2.pulsar:6651,broker3.pulsar:6651`
         
Troubleshooting 

`ansible -i inv all -m shell -a "ls /opt" -u vagrant --become`

Execute the playbook

`ansible-playbook deploy-pulsar.yml -i inv -u vagrant --become`

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).

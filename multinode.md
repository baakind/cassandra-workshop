# Multi node cluster #
_Todo:_

1. Definere tre seed-noder
2. Avklare Opscenter ip
3. Finne egen ip og markere sin maskin med denne vha post-it

## Installere Datastax-agent ##
* Laste ned [Datastax Agent 5.1.0](http://downloads.datastax.com/community/datastax-agent-5.1.0.tar.gz)
* unpack
* cd datastax-agent-5.1.0
* `echo "stomp_interface: <opscenter-maskin-ip>" >> ./conf/address.yaml`
* bin/datastax-agent -f


## Init cluster ##
* Slett data fra
	* /data
	* /commitlog
	* /saved_caches
* Editer conf/cassandra.yaml
	* seeds: liste av tre noder (bestemmes på workshopen, starter først)
	* listen_address: din ip
	* rpc_address: din ip
	
### I plenum ###
* Seed noder starter først (bin/cassandra -f -> waiting for thrift clients...)
* Visualsering vha OpsCenter
	* [Localhost](http://localhost:8888) 
* Start flere noder
* Insert data
	* bin/cqlsh -f playlist.cql (datasett-multinode)
* Starte resterende noder
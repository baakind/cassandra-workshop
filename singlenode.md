# Single node cluster #


## Start Cassandra ##
* Last ned [Cassandra](http://planetcassandra.org/cassandra/)
	* Tarball 2.0.12 
* Unzip
* Editer conf/cassandra.yaml
	* cluster_name: 'BEKK Workshop'
	* data_files_directories: ./cassandra-data/data
	* commitlog_directory: ./cassandra-data/commitlog
	* saved_caches_directory: ./cassandra-data/saved_caches
* Editer conf/log4j-server.properties
	* log4j.appender.R.File=./cassandra-data/system.log
* bin/cassandra -f 


## Interagere med clusteret ##
* Nytt terminalvindu
* bin/cqlsh
	* `DESCRIBE keyspaces`
	* `USE system`
	* `DESCRIBE tables`
	* `DESCRIBE TABLE batchlog`
	* `exit`
* bin/nodetool \<kommando\> (blank = help)
	* status
	* info
	* andre kommandoer som repair, compaction etc.
	
## Importere data ##
* unpack `datasett-singlenode.tar.gz`
* bin/cqlsh -f datasett/playlist.cql
* bin/cqlsh
	* `DESCRIBE keyspaces`
	* `USE playlist`
	* `DESCRIBE tables`
	* `DESCRIBE TABLE track_by_artist`
	* `SELECT * FROM track_by_artist LIMIT 10`
	* `SELECT * FROM track_by_artist WHERE artist = 'Lee Greenwood';`
	* `SELECT * FROM track_by_artist WHERE track = 'America';`
		* Hva skjedde?
		* ALLOW FILTERING
	* `SELECT * FROM track_by_artist WHERE artist = 'Lee Greenwood' AND track = 'America';`
	* `exit`
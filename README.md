<h1>OpenSuse 12.3 docker for Synthese</h1>

Note : all path are relative from /opt/data inside the docker
To map the docker instance's /opt/data to a local directory outside the docker instance use :

<pre>
docker run -i -t -v /absolute/local/path:/opt/data ...
</pre>


<h2>Usage</h2>
help 		 Show this help message 
db=XXX 		 Load this synthese database at start 
bdsi=XXX 	 Load this BDSI database at start 
install=XXX 	 Install the Synthese software from this file (tar.bz2 or tar.gz) 
autoload 	 If this flag is given, the synthese database will be loaded from /opt/data/synthese.sql, the bdsi from /opt/data/bdsi.sql and the executable from /opt/data/synthese.tar.bz2. Any file not found will be ignored.
bash 		 Will run /bin/bash instead of synthese, ignoring every other parameters
run XXX 	 Will run the arguments as an exectuable and its parameters 
gdb 		 Will run Synthese under GDB
save=XXX	 Will save the database after s3-server is stopped to /opt/data/XXX

All the other parameters will be directly passed to the s3-server executable.
If no arguments are given for s3-server, the default one will be used : 
<pre>
--dbconn mysql://host=localhost,user=synthese,passwd=synthese,db=synthese --pidfile - --param node_id=100 --param log_level=0 --param port=8080
</pre>


<h2>Examples</h2>

Run a simple hello world instead of Synthese :
<pre>
run echo hello world
</pre>

Run synthese with default parameters (use mysql connexion):
<pre>
(no arguments)
</pre>

Run a specific Synthese executable with the specified database (which are in /opt/data):
<pre>
install=synthese.tar.bz2 db=synthese.sql
</pre>

# CassandraOnWindows
Tools, scripts, configurations, and instructions related to running Cassandra on Microsoft Windows.

### Docker Desktop
Meant to be used with [Docker Desktop](https://www.docker.com/products/docker-desktop).  Follow the instructions at this link to install.

Verify your Docker installation/version with this command:

    docker --version

    Docker version 20.10.8 3967b7d

### Pull down Docker Cassandra image
Download the Cassandra image using the `docker pull` command.  Indicate "cassandra" followed by a colon (":") and the desired version number:

    docker pull cassandra:4.0

### Starting Cassandra
To start the container with a default configuration, simply execute the `docker run` command:

    docker run --name my-cassandra -d cassandra:4.0

If you want the container to be able to accept connections from an application or client (example: local development), be sure to bind on port 9042.

    docker run --name my-cassandra -d -p 9042:9042 cassandra:4.0

Once the node is up, you should get a good response from running a `nodetool status`:

    docker exec -it my-cassandra nodetool status

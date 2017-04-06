## Overview
**NOTE:** This Dockerfile is copied from [couchbase/docker](https://github.com/couchbase/docker/blob/master/community/couchbase-server/4.5.0) and contains modifications to make it more friendly for CI testing.  
- VOLUME removed, data will not persist when the container restarts (without manual VOLUME configuration)
- Cluster and bucket are configured during docker build
	- Username: Administrator
	- Password: password
	- RAM: 256M
	- Bucket: default

## Usage
To build the couchbase-server container with default values:

`docker build -t couchbase-server .`

To build the couchbase-server container with a 512MB bucket named testing:

`docker build --build-arg RAM_SIZE_MB=512 --build-arg BUCKET=testing -t couchbase-server .`

To run the couchbase-server container:

`docker run -d --rm --name couchbase-server -p 8091-8094:8091-8094 -p 11210-11211:11210-11211 couchbase-server`

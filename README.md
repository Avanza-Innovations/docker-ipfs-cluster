﻿# standalone-ipfs-cluster-docker
The ipfs cluster has to be altered to make it work with other peers. So, one node needs to be initialized first [This docker-compose file is in master branch]. Then other nodes will initialized based on cluster details of the first node located in defined-cluster branch.
Steps:
1.	Docker-compose run the first node
2.	Go to /data/ipfs-cluster or whichever mapped location
3.	Open service.json
4.	In Other nodes folder at location Other nodes\individual\cluster\run.sh
5.	Change “/cluster daemon --bootstrap /ip4/<ip of other node>/tcp/9096/ipfs/<cluster id of other node>” with 
6.	Run the docker-compose file in the other node
7.	After running docker-compose, a service.json file will be created in the same location as the first node for the second node. Go there and change private_key field to match with the private_key of the first node. This is the magic that prevents others from joining in a cluster.
8.	Docker restart the containers

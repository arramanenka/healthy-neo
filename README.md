Neo4j is nosql graph database with native graph storage and processing.
This is a simple wrapper around neo4j docker image with basic healthcheck. 
script for healthceck was taken from https://neo4j.com/docs/operations-manual/current/configuration/wait-for-start/
Once run in docker with exposed port 7474, you can access simple neo4j browser via http://localhost:7474/browser/

Important:
- for login/password, set env variable NEO4J_AUTH=login/password
- for additional plugins, set env variable NEO4JLABS_PLUGINS=["graph-algorithms", "apoc"]
- to permit using those plugins outside of sandbox, set env variable NEO4J_dbms_security_procedures_unrestricted=algo\.\*

If you d far rather just run neo4j in docker but can't seem to find proper command for running with plugins:
```
docker run \
    --name healthy-neo \
	--env NEO4J_AUTH=none \
    --env NEO4JLABS_PLUGINS=["graph-algorithms"] \
    --env NEO4J_dbms_security_procedures_unrestricted=algo\.\* \
    neo4j:latest
```

This image is also available in docker hub, please see: https://hub.docker.com/repository/docker/arramanenka/dumpster

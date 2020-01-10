FROM neo4j:latest
RUN apt-get update && apt-get -y install netcat && apt-get clean
HEALTHCHECK CMD end="$((SECONDS+60))"; while true; do nc -w 2 localhost 7687 && break; [[ "$((SECONDS))" -ge "${end}" ]] && exit 1; sleep 1; done
CMD ["neo4j"]
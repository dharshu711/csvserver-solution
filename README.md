
# The csvserver

## Commands:
- **Clone this repository to your machine and cd into the solution directory and perform all the steps from that directory**

- **Docker images pull command:**
```
docker pull infracloudio/csvserver:latest
docker pull prom/prometheus:v2.45.2
```
```
- docker images
REPOSITORY               TAG       IMAGE ID       CREATED        SIZE
infracloudio/csvserver   latest    54e5b35bc16f   11 months ago   215MB
prom/prometheus          v2.45.2   9c9cea65ba17   11 months ago   238MB

```

- **Bash script gencsv.sh**

-> cat gencsv.sh
```
#!/bin/bash

if [ $# -ne 2 ]; then
    echo "Usage: $0 <start> <end>"
    exit 1
fi

start=$1
end=$2

for i in $(seq $start $end)
do
    echo "$i, $RANDOM" >> inputFile
done
```
- **Bash script output:**

-> cat inputdata
```
2, 22747
3, 5308
4, 18119
5, 19562
6, 23744
7, 24287
8, 31441

```
- **Docker run command:**
```
docker run -d --name csvserver -e CSVSERVER_BORDER='Orange' -v ${PWD}/inputdata:/csvserver/inputdata -p 9393:9300 infracloudio/csvserver
```

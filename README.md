# gist_resources
repo for resources used in gitsts

```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```

# MY DEV Env

```
docker exec -it allspark bash
```

##### [Structurizr On-Premises](https://docs.structurizr.com/onpremises/installation)

```
docker pull structurizr/onpremises
```

```
docker run -it --rm \
 -p 8881:8080 \
 -v ${DOCPATH}:/usr/local/structurizr \
 --name "onprem"
 structurizr/onpremises
```


##### [Structurizr Lite](https://structurizr.com/share/76352/documentation)

```
#
docker pull structurizr/lite

#
cd XXX;

#
export DOCPATH=`pwd`; ls $DOCPATH; \
echo "Press any key to continue"; read; \
history |grep -E "structur|my-apache";

#
docker run -dit --rm \
 -p 8891:8080 \
 -v ${DOCPATH}:/usr/local/structurizr \
 --name "structurizr" \
 structurizr/lite
```

* http://10.8.9.33:8891


##### [Apache httpd for dbt doc](https://hub.docker.com/_/httpd)

```
#
cd XXX;

#
export DOCPATH=`pwd`; ls $DOCPATH; \
echo "Press any key to continue"; read; \
history |grep -E "structur|my-apache";

#
docker run -dit --rm \
 -p 9001:80 \
 -v ${DOCPATH}:/usr/local/apache2/htdocs/ \
 --name my-apache-app \
 httpd:2.4
```

##### [Apache Spark Notebook](https://hub.docker.com/r/jupyter/all-spark-notebook)


* spark-2
```
#
sudo docker container stop allspark

#
sudo docker exec -it allspark bash

#
docker run \
 --memory=1024m \
 --cpus=0.9 \
 --detach \
 --publish 8890:8888 \
 --publish 4040:4040 \
 --publish 9000:9000 \
 --user root \
 --name "allspark" \
 -v /home/jupyter:/home/jovyan/work \
 --env JUPYTER_ENABLE_LAB=yes \
 --env GRANT_SUDO=yes \
 jupyter/all-spark-notebook:77e10160c7ef \
 start-notebook.sh \
 --NotebookApp.password='sha1:c47b3322a3ee:74908547b0e99449de557de82f64e72cd6051acb'
```

* spark-3.1.2

```
docker run \
 --memory=1024m \
 --cpus=0.9 \
 --detach \
 --publish 8890:8888 \
 --publish 4040:4040 \
 --publish 9000:9000 \
 --user root \
 --name "allspark2" \
 -v /home/jupyter:/home/jovyan/work \
 --env JUPYTER_ENABLE_LAB=yes \
 --env GRANT_SUDO=yes \
 jupyter/all-spark-notebook:spark-3.1.2 \
 start-notebook.sh \
 --NotebookApp.password='sha1:c47b3322a3ee:74908547b0e99449de557de82f64e72cd6051acb'
```

##### [Microsoft SQL Server - Ubuntu based images](https://hub.docker.com/_/microsoft-mssql-server)

```
#
docker run -d \
 -e "ACCEPT_EULA=Y" \
 -e "MSSQL_SA_PASSWORD=mssql12345MSSQL" \
 -p 1433:1433  \
 --name mymssql \
 mcr.microsoft.com/mssql/server:2019-latest; \
sleep 3; \
docker container logs mymssql;

#
docker exec -it mymssql /opt/mssql-tools/bin/sqlcmd -S localhost -U sa -P mssql12345MSSQL

#
docker container stop mymssql; \
sleep 3;\
docker container rm mymssql
```


# Install Elasticsearch amb les Dependencies
## Install Docker
Docker és un contenidor que permet instalar blabla (completar).
Primer de tot instal·lar docker & docker compose segons cada S.O que tingueu. [docker](https://docs.docker.com/install/)

Un cop instal·lat els 2 (docker & docker compose)-->

## Fer un git clone del project.
Fem un git clone del projecte a la nostra maquina local, tots ho hem fet a pds o caes...

## Build Containers
Dins la carpeta del projecte->
With Docker installed, build the containers as below. You only need to do this once.
```bash
cd es-docker
docker build --tag=elasticsearch-tlre .
cd ../kb-docker
docker build --tag=kibana-tlre .
```
## Executem el Contenidor.

```bash
docker-compose up
```
Se'ns obrirà una consola on veurem que s'esta engegant el elastic i el kibana, la deixem oberta no la tenquem, es quedara aixi perque va traient logs i altres coses. (La minimitzem).

## Comprovem que elastic & Kibana s'estiguin executan correctament.
Browse to http://localhost:9200 and http://localhost:5601 to confirm ES / Kibana running

# Indexar DB movies. (IN PROGRESS DONT DOWNLOAD)
Un cop instal·lat E.S. & Kibana anem a indexar la DB de movies perque el elastic les pugui afegir.
1. Descargar la DB amb la que treballarem --> Download [tmdb.json](http://es-learn-to-rank.labs.o19s.com/tmdb.json) Es tocha de collons 123MB ojoo el pc!

2. Hem d'installar Phynton 3.6 per a poder executar el script que he trobat a interneh i la llibreria de ...





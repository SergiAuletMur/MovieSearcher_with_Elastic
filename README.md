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

# Indexar DB movies.
Un cop instal·lat E.S. & Kibana anem a indexar la DB de movies perque el elastic les pugui afegir.
1. Descargar la DB amb la que treballarem --> Download [tmdb.json](http://es-learn-to-rank.labs.o19s.com/tmdb.json) Es tocha de collons 123MB ojoo el pc!

2. Hem d'installar Phynton 3.6 o 3.7 per a poder executar el script que he trobat a interneh
- Per Ubuntu:
```bash
sudo apt update
sudo apt install python3.6
```
Mirem versio que sens ha instalat:
```bash
python -V
```
A mi mha sortit versio 2.17 o algo aixi i mha xutat igualment aixi que prubeu.

- Per Windows:
https://www.python.org/downloads/

3. Instalem llibreria de elastic per Python. [llibreria](https://elasticsearch-py.readthedocs.io/en/master/)
Esta en ubuntu en windows npi, busqueu google nse perq feu servir windows xD.

4. Executar script.
Aquest script indexa i afegeix a elastic veureu a la consola que es van indexant i afegint, pero tarda la vida perque la database json es de 123MB.

```bash
python indexTmdb.py
```

OJO: El indexar l'he tret tot de internet (copy & paste) haurem de mirar cada fitxer per entendre que per el dia de la expo.

Mho he mirat per sobre yo coses que he anat entenent:
El script indexa i afegeix a la DB.
Els json_schema serveixen per definir-li la estrucutura que tindran els camps index (no ho ser segur):
  Exemple:
  ```bash
  {
    _index,
    _type,
    cluster{
      node1
      node2
   }
   {
    Aqui aniria les dades de la pelicula.
   }
  }
```
  Per tant cada objecte pelicula al executar el script tindra aquets camps que segiran el patro del json_schema.
  Mho he mirat per sobre sha de aprofondir...

## Probar que haguem afegit les pelis

 Navegueu [aqui](http://localhost:9200/tmdb/_search?q=*)
Us ha de sortir un llistat de pelis que hi ha al Elastic, nose si totes ami men surten 5 o 6 he de mirar pq si esta be o que esta pasant

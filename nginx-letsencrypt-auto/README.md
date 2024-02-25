# Steps
1. Create a docker network. (docker network create nginx)
2. Start the docker file.


## APP DOCKER-COMPOSE FOR IT TO WORK.
The cruical part is the docker-compose.yml file is the env vars.
environment:
    - VIRTUAL_HOST=<DOMAIN>
    - LETSENCRYPT_HOST=<DOMAIN>
    - LETSENCRYPT_EMAIL=<EMAIL>

'''
# docker-compose.yml
version: '3'

services:
  jupyter:
    image: jupyter/base-notebook
    container_name: jupyter-notebook
    environment:
      - VIRTUAL_HOST=<DOMAIN>
      - LETSENCRYPT_HOST=<DOMAIN>
      - LETSENCRYPT_EMAIL=<EMAIL>
    volumes:
      - /home/ubuntu:/home/jovyan/work
    networks:
      - nginx-proxy

networks:
  nginx-proxy:
    external: true
'''

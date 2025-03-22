WP_DATA = /home/oabdelka/data/wordpress #define the path to the wordpress data
DB_DATA = /home/oabdelka/data/mariadb #define the path to the mariadb data# default target

all: up # start the building process
# create the wordpress and mariadb data directories.
# start the containers in the background and leave them running

up: build
	@mkdir -p $(WP_DATA)
	@mkdir -p $(DB_DATA)
	docker compose -f ./srcs/docker-compose.yml up -d

down:
	docker compose -f ./srcs/docker-compose.yml down

stop:
	docker compose -f ./srcs/docker-compose.yml stop

start:
	docker compose -f ./srcs/docker-compose.yml start

build:
	docker compose -f ./srcs/docker-compose.yml build

# stop all running containers and remove them.
# remove all images, volumes and networks (excluding predefined networks).
# remove the wordpress and mariadb data directories.

clean:
	@docker stop $$(docker ps -qa) || true
	@docker rm $$(docker ps -qa) || true
	@docker rmi -f $$(docker images -qa) || true
	@docker volume rm $$(docker volume ls -q) || true
	@docker network rm $$(docker network ls -q) || true
	@rm -rf $(WP_DATA) || true
	@rm -rf $(DB_DATA) || true# clean and start the containers

re: clean up# PHONY rules to avoid naming conflicts with real files

.PHONY: all up down stop start build clean re
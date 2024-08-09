COMPOSE_CMD = docker-compose
COMPOSE_FILE = local.yml
COMPOSE = $(COMPOSE_CMD) -f $(COMPOSE_FILE)

all: down build up

build:
	$(COMPOSE) build django
ifeq ($(INCLUDE_PGADMIN),true)
	$(COMPOSE) build pgadmin
endif

up:
	$(COMPOSE) up django --detach
ifeq ($(INCLUDE_PGADMIN),true)
	$(COMPOSE) up pgadmin --detach
endif

down:
	$(COMPOSE) down
	docker ps -a

l:
	$(COMPOSE) logs $(DJANGO_CONTAINER)

dau: down up
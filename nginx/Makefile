IMAGE=$(shell basename $(shell pwd))
TAG=1.0
REGISTRY=registry.hub.docker.com
REGISTRY_USER=blade2iron

FQIN=$(REGISTRY_USER)/$(IMAGE)

build:
	docker build -t $(FQIN)  .

rmi:
	docker rmi -f $(FQIN)
	docker rmi -f $(FQIN):latest
	docker rmi -f $(FQIN):$(TAG)

install:
	@echo "TBD."

test:
	@echo "TBD."

clean:
	@echo "TBD."

publish:
	docker login -u ${REGISTRY_USER} $(REGISTRY)
	docker tag  $(FQIN) $(FQIN):latest
	docker push $(FQIN):latest
	docker tag  $(FQIN) $(FQIN):$(TAG)
	docker push $(FQIN):$(TAG)
	@echo "RUN exmaple:"
	@echo "docker run --rm -p 80:80  $(FQIN):latest"
	@echo "docker run --rm -it -p 80:80 $(FQIN):latest bash"

publish-test:
	docker search $(FQIN)

all: build publish publish-test

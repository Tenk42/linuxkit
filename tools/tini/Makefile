.PHONY: tag push
default: push

IMAGE=tini
DEPS=Dockerfile

HASH?=$(shell git ls-tree HEAD -- ../$(notdir $(CURDIR)) | awk '{print $$3}')

tag: $(DEPS)
	docker build --no-cache --network=none -t linuxkit/$(IMAGE):$(HASH) .

push: tag
	DOCKER_CONTENT_TRUST=1 docker pull linuxkit/$(IMAGE):$(HASH) || \
	DOCKER_CONTENT_TRUST=1 docker push linuxkit/$(IMAGE):$(HASH)

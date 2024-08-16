VERSION = 4.2.4.1
DOCKER_REPO = gatk

SHORT_HASH := $(shell git rev-parse --short HEAD)
DOCKER_URL := ghcr.io/${GHCR_NAMESPACE}
DOCKER_IMAGE := ${DOCKER_URL}/${DOCKER_REPO}:${VERSION}
DOCKER_IMAGE_HASH := ${DOCKER_URL}/${DOCKER_REPO}:${VERSION}-${SHORT_HASH}

.PHONY: version version-* name
name:
	@echo ${NAME}

version:
	@echo --- VERSION: ${VERSION} ---

version-docker:
	@echo ${DOCKER_IMAGE_COMMIT}
	@echo ${DOCKER_IMAGE}

.PHONY: build build-*
build: build-docker

build-docker:
	@echo
	@echo -- Building docker --
	docker build . \
		--file ../Dockerfile.multi \
		--build-arg VERSION=${VERSION} \
		-t "${DOCKER_IMAGE}" \
		-t "${DOCKER_IMAGE_HASH}"
		
publish: 
	@echo
	@echo -- Publishing docker --
	docker push "${DOCKER_IMAGE}"
	docker push "${DOCKER_IMAGE_HASH}"
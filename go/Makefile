PROJECT = wetron-mqtt-backend

default: build

build:
	docker build -t $(PROJECT) .
	docker run --rm -v ${PWD}:/usr/src/app -w /usr/src/app $(PROJECT):latest go build -v

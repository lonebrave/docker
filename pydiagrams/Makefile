NAME = nickhasser/pydiagrams
VERSION = 0.0.1
LOCALDIR = `pwd`

default: build

clean:
	docker image rm $(NAME)

build:
	docker build -t $(NAME):$(VERSION) .

build-latest:
	docker build -t $(NAME) .

push:
	docker push $(NAME):$(VERSION)

push-latest:
	docker push $(NAME)

debug:
	docker run --rm -it -v $(LOCALDIR):/tmp/hostdir $(NAME) /bin/bash

run:
	docker run --rm $(NAME)

release: build push

release-latest: build-latest push-latest

update-req:
	sed -e 's/==.*//' ../pydev/requirements.txt > pydev_req_nover.txt
	sed -e 's/==.*//' requirements.txt > pynet_req_nover.txt
	grep -w -v -f pydev_req_nover.txt pynet_req_nover.txt > requirements.txt
	rm pydev_req_nover.txt pynet_req_nover.txt

update-req-ver:
	grep -w -v -f ../pydev/requirements.txt requirements.txt > pynet_req.txt
	mv pynet_req.txt requirements.txt

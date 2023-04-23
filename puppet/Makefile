VOLUMES=-v ${PWD}/r10k/etc_puppetlabs_r10k/r10k.yaml:/etc/puppetlabs/r10k/r10k.yaml -v ${PWD}/r10k/var_cache_r10k:/var/cache/r10k/ -v ${PWD}/puppet/etc_puppetlabs_code/:/etc/puppetlabs/code/ -v ${PWD}/r10k/home_puppet_.ssh/:/home/puppet/.ssh/
NAME=r10k
IMAGE=puppet/r10k
VERSION=3.15.2
CMD=deploy environment --color --verbose=debug2 --modules
r10k-setup:
	mkdir -p ${PWD}/r10k/etc_puppetlabs_r10k
	mkdir -p ${PWD}/r10k/home_puppet_.ssh
	mkdir -p ${PWD}/r10k/var_cache_r10k
	mkdir -p ${PWD}/puppet/etc_puppetlabs_code
	touch ${PWD}/r10k/etc_puppetlabs_r10k/r10k.yaml
	touch ${PWD}/r10k/home_puppet_.ssh/id_rsa
	touch ${PWD}/r10k/home_puppet_.ssh/id_rsa.pub
	ssh-keyscan gitlab.com > ${PWD}/r10k/home_puppet_.ssh/known_hosts
	sudo chown -R 999:999 r10k puppet
	sudo chmod -R 700 r10k/home_puppet_.ssh

r10k-debug:
	docker run -it ${VOLUMES} --rm --name ${NAME} --entrypoint=/bin/ash ${IMAGE}:${VERSION}

r10k-run:
	docker run -it ${VOLUMES} --rm --name ${NAME} ${IMAGE}:${VERSION} ${CMD}
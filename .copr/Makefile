SPEC_DIR := $(shell dirname $(shell readlink -e $(spec)))
OPTIONS := \
	--define "_rpmdir $(outdir)" \
	--define "_sourcedir $(SPEC_DIR)" \
	--define "_srcrpmdir $(outdir)"  \

srpm: prepare
	rpmbuild -bs $(OPTIONS) $(spec)

rpm: prepare
	rpmbuild -bb $(OPTIONS) $(spec)

prepare:
	dnf -y install fedpkg rpmdevtools rpm-build || true
	fedpkg --name kernel sources
	spectool -g --directory $(SPEC_DIR) $(spec)

.PHONY: prepare srpm rpm

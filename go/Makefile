ROOT_DIR := $(dir $(realpath $(lastword $(MAKEFILE_LIST))))

build:
	make -C ../c build
	CGO_LDFLAGS="$(ROOT_DIR)../c/libsputnikvm.a -ldl -lssl -lcrypto -lpthread -lm" go build main.go

run: build
	./main

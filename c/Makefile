ifdef OS
	LIB=lib
	DLL=dll
else
	PREFIX=lib
	LIB=a
	DLL=so
endif

build:
	cd ffi && cargo build --release --no-default-features --features "std rlp"
	cp ffi/target/release/$(PREFIX)sputnikvm_ffi.$(LIB) $(PREFIX)sputnikvm.$(LIB)
	cp ffi/target/release/$(PREFIX)sputnikvm_ffi.$(DLL) $(PREFIX)sputnikvm.$(DLL) | true

build-musl:
	cd ffi && docker run --rm -it -v "$(shell pwd)/ffi":/home/rust/src ekidd/rust-musl-builder cargo build --release
	cp ffi/target/x86_64-unknown-linux-musl/release/$(PREFIX)sputnikvm_ffi.$(LIB) $(PREFIX)sputnikvm.$(LIB)

debug:
	cd ffi && cargo build
	cp ffi/target/debug/$(PREFIX)sputnikvm_ffi.$(LIB) $(PREFIX)sputnikvm.$(LIB)
	cp ffi/target/debug/$(PREFIX)sputnikvm_ffi.$(DLL) $(PREFIX)sputnikvm.$(DLL) | true

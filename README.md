# WasmGNUDiff

Port GNU’s diffutils-3.8 to wasm using emscripten.


## Steps to build `diff.wasm`

Environment: macOS Monterey 12.3.1, Xcode 13.3, x86_64

```shell
git clone https://github.com/juj/emsdk.git
cd emsdk

./emsdk install latest
./emsdk activate latest
source ./emsdk_env.sh

wget https://ftp.gnu.org/gnu/diffutils/diffutils-3.8.tar.xz
wget https://ftp.gnu.org/gnu/diffutils/diffutils-3.8.tar.xz.sig

mkdir diffutils
tar xzvf diffutils-3.8.tar.xz -C diffutils
cd diffutils/diffutils-3.8

emconfigure ./configure
emmake make
cp src/diff.wasm ../../
```


## Issues

If you encounter the problem https://github.com/emscripten-core/emscripten/issues/12415:

- Locate line `configure:44001`, insert `return 0;` before this line.
- Locate line `configure:42282`, insert `return 0;` before this line.

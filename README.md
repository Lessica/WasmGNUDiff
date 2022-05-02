# WasmGNUDiff

Port GNU’s diffutils-3.8 to wasm using emscripten.


## Steps to build `diff.wasm`

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

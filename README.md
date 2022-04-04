Element - Tauri
======================


## Disclaimer

This is a fork of element demonstrating how to package element-web with [tauri](https://tauri.studio).
This is a demo, and you should probably not be your default matrix client.
Currently, only building element 1.9.9 for the sake of demonstration, synchronisation with element-web upstream
will comme later.

## How to ?

### Prerequisites
 - All the prerequisites listed on [element-web's readme ](https://github.com/vector-im/element-web) apply
 - Additionally, you need to [install the rust toolchain](https://www.rust-lang.org/tools/install)

1. create a valid config.json file (see: https://github.com/vector-im/element-web/blob/develop/docs/config.md)

2. package element as you would normally do :
```shell
yarn install
yarn dist
```

3. extract the source directory and copy the config file :
```shell
cd dist
tar -xvf element-v1.9.9-dirty.tar.gz
cp ../config.json element-v1.9.9-dirty/
```

4. build the native app :
```shell
yarn tauri build
```

5. run :
```shell
./src-tauri/target/release/bundle/appimage/{image}
```

## Things we need to do before packaging a release

- automate packaging to keep up with element-web upstream
- test the every possible feature, SSO, desktop notification, file system integration etc.
- reduce the app size (see: https://tauri.studio/docs/building/app-size).
- system tray support (see: https://tauri.studio/docs/guides/system-tray).
- cross compilation (currently we have just tested to build a linux image).

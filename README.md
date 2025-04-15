# glibc2.28_for_CentOS7
# failed if zsh is the default shell

## Usage:
```bash
tar -xf lib.tgz
```
then set following in ~/.bashrc
```bash
export TOOLCHAIN_DIR=/path/to/glibc2.28_for_CentOS7  # MODIFY THIS!
export TOOLCHAIN_VERSION=2.28
export VSCODE_SERVER_CUSTOM_GLIBC_LINKER=${TOOLCHAIN_DIR}/lib/ld-${TOOLCHAIN_VERSION}.so
export VSCODE_SERVER_CUSTOM_GLIBC_PATH=${TOOLCHAIN_DIR}/lib
export VSCODE_SERVER_PATCHELF_PATH=${TOOLCHAIN_DIR}/bin/patchelf
```
then your vscode 1.99 work well

## Introduction:
this sysroot was compiled by ct-ng on CentOS7.9
glibc 2.28 was compiled with 3.10 kernel
patchelf is 0.15

## Suggestions:
I have failed to install a ct-ng sysroot on a cluster due to the compicate environments.
Then I realized that the minimal "lib" dir and a patchelf binary are good for a new CentOS7.
For security, you can compile your own sysroot by ct-ng in a clean CentOS7.9 virtual machine, tar it, copy to target machine, tar -xf.

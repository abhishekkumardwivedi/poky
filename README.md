# poky

## Check hello world in sdk
## eSDK
Get toolchin and do setup.
`wget http://downloads.yoctoproject.org/releases/yocto/yocto-2.1/toolchain/x86_64/poky-glibc-x86_64-core-image-sato-core2-64-toolchain-ext-2.1.sh`
`chmod +x poky-*.sh`
`./poky-glibc-x86_64-core-image-sato-core2-64-toolchain-ext-2.1.sh`
`cd poky_sdk`
`source environment-setup-core2-64-poky-linux`
`devtool --help`

Let's begin with faster way, download qemu image in sdk folder

`wget http://downloads.yoctoproject.org/releases/yocto/yocto-2.2/machines/qemu/qemux86-64/core-image-sato-dev-qemux86-64.ext4`

If you have done git pull for the readme, you will get sample example as well, let's check that here now.

## References
* http://www.yoctoproject.org/docs/current/sdk-manual/sdk-manual.html
* https://mender.io/resources/yocto-sdk-quickstart

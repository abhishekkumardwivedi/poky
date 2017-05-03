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


## To build eSDK from existing source
`
$bitbake <image> -c populate_sdk_ext
`

## What SDK supposed to contain
If we refer yoctoproject sdk manual, description given is,

You can use the standard SDK to independently develop and test code that is destined to run on some target machine.

An extensible SDK consists of everything that the standard SDK has plus tools that allow you to easily add new applications and libraries to an image, modify the source of an existing component, test changes on the target hardware, and easily integrate an application into the OpenEmbedded build system.

SDKs are completely self-contained. The binaries are linked against their own copy of libc, which results in no dependencies on the target system. To achieve this, the pointer to the dynamic loader is configured at install time since that path cannot be dynamically altered. This is the reason for a wrapper around the populate_sdk and populate_sdk_ext archives.

Another feature for the SDKs is that only one set of cross-compiler toolchain binaries are produced per architecture. This feature takes advantage of the fact that the target hardware can be passed to gcc as a set of compiler options. Those options are set up by the environment script and contained in variables such as CC and LD. This reduces the space needed for the tools. Understand, however, that a sysroot is still needed for every target since those binaries are target-specific.

The SDK development environment consists of the following:

* The self-contained SDK, which is an architecture-specific cross-toolchain and matching sysroots (target and native) all built by the OpenEmbedded build system (e.g. the SDK). The toolchain and sysroots are based on a Metadata configuration and extensions, which allows you to cross-develop on the host machine for the target hardware.

* The Quick EMUlator (QEMU), which lets you simulate target hardware. QEMU is not literally part of the SDK. You must build and include this emulator separately. However, QEMU plays an important role in the development process that revolves around use of the SDK.

* The Eclipse IDE Yocto Plug-in. This plug-in is available for you if you are an Eclipse user. In the same manner as QEMU, the plug-in is not literally part of the SDK but is rather available for use as part of the development process.

* Various user-space tools that greatly enhance your application development experience. These tools are also separate from the actual SDK but can be independently obtained and used in the development process.

## References
* http://www.yoctoproject.org/docs/current/sdk-manual/sdk-manual.html
* https://mender.io/resources/yocto-sdk-quickstart

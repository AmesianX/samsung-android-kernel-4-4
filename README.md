```
Kernel$ apt-get install -y gcc-aarch64-linux-gnu bc
Kernel$ dos2unix drivers/sensorhub/brcm/bbdpl/Kconfig
Kernel$ ARCH=arm64 ANDROID_MAJOR_VERSION=7 CROSS_COMPILE=aarch64-linux-gnu- make exynos8895-dreamlte_eur_open_defconfig
Kernel$ ARCH=arm64 ANDROID_MAJOR_VERSION=7 CROSS_COMPILE=aarch64-linux-gnu- make -j 4

If an error occurs, modify the following options.

Kernel$ vi scripts/Makefile.build

EXTRA_CFLAGS := -D__ANDROID__ -Wno-error=array-bounds -Wno-error=logical-not-parentheses -Wno-error=switch-bool -Wno-error=unused-variable


###############################################
The following are optional options when needed.
It is rarely needed for beginners.
###############################################
CONFIG_KCOV=y
CONFIG_KCOV_INSTRUMENT_ALL=y
CONFIG_DEBUG_FS=y
CONFIG_DEBUG_INFO=y
CONFIG_NAMESPACES=y
CONFIG_USER_NS=y
CONFIG_UTS_NS=y
CONFIG_IPC_NS=y
CONFIG_PID_NS=y
CONFIG_NET_NS=y
CONFIG_KASAN=y
CONFIG_KASAN_INLINE=y
CONFIG_LOCKDEP=y
CONFIG_PROVE_LOCKING=y
CONFIG_DEBUG_ATOMIC_SLEEP=y
CONFIG_PROVE_RCU=y
CONFIG_DEBUG_VM=y
CONFIG_RCU_CPU_STALL_TIMEOUT=60
CONFIG_CMDLINE=”console=ttyAMA0”
CONFIG_NET_9P=y
CONFIG_NET_9P_VIRTIO=y
CONFIG_CROSS_COMPILE="aarch64-linux-gnu-"


################################################################################
Samsung Android/Linux kernel 4.4

Extracted from SM-G950F_NN_Opensource.zip from Samsung Opensource center

Jun 8, 2017

daveti
################################################################################

1. How to Build
	- get Toolchain
		From android git server , codesourcery and etc ..
		 - arm-eabi-4.9
		
	- edit Makefile
		edit "CROSS_COMPILE" to right toolchain path(You downloaded).
		  EX)  CROSS_COMPILE= $(android platform directory you download)/android/prebuilts/gcc/linux-x86/arm/arm-eabi-4.9/bin/arm-eabi-
		  Ex)  CROSS_COMPILE=/usr/local/toolchain/arm-eabi-4.9/bin/arm-eabi-		// check the location of toolchain
  	
        - to Build
          $ make ARCH=arm64 exynos8895-dreamlte_eur_open_defconfig
          $ make ARCH=arm64

2. Output files
	- Kernel : arch/arm/boot/zImage
	- module : drivers/*/*.ko

3. How to Clean	
		$ make clean
################################################################################
```

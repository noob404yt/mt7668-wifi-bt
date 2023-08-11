KERNEL_SRC=/lib/modules/kernel_version/build
ARCH=x86
SDIO_MOD_NAME = bt_mt7668
SDIO_CFILES := \
	btmtk_sdio.c btmtk_main.c
$(SDIO_MOD_NAME)-objs := $(SDIO_CFILES:.c=.o)
obj-m := $(SDIO_MOD_NAME).o

all:
	$(MAKE) EXTRA_CFLAGS="-w" ARCH=$(ARCH) CROSS_COMPILE=$(CROSS_COMPILE) -C $(KERNEL_SRC) M=$(PWD) modules

clean:
	rm -f *.o *~ core .depend .*.cmd *.ko *.mod.c
	rm -f Module.markers Module.symvers modules.order
	rm -rf .tmp_versions Modules.symvers

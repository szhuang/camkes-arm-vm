#
# Copyright 2014, NICTA
#
# This software may be distributed and modified according to the terms of
# the BSD 2-Clause license. Note that NO WARRANTY is provided.
# See "LICENSE_BSD2.txt" for details.
#
# @TAG(NICTA_BSD)
#

TARGETS := $(notdir ${SOURCE_DIR}).cdl
ADL := vm.camkes

pilot_CFILES := \
    $(patsubst ${SOURCE_DIR}/%,%,$(wildcard ${SOURCE_DIR}/components/pilot/src/*.c)) \
    $(patsubst ${SOURCE_DIR}/%,%,$(wildcard ${SOURCE_DIR}/components/pilot/src/aeslib/*.c))

pilot_HFILES := \
    $(patsubst ${SOURCE_DIR}/%,%,$(wildcard ${SOURCE_DIR}/components/pilot/src/aeslib/*.h))

uart_CFILES := \
    $(patsubst ${SOURCE_DIR}/%,%,$(wildcard ${SOURCE_DIR}/components/uart/src/*.c))

gpio_HFILES := \
    $(patsubst ${SOURCE_DIR}/%,%,$(wildcard ${SOURCE_DIR}/include/*.h))
gpio_CFILES := \
    $(patsubst ${SOURCE_DIR}/%,%,$(wildcard ${SOURCE_DIR}/components/gpio/src/*.c))

pwm_CFILES := \
    $(patsubst ${SOURCE_DIR}/%,%,$(wildcard ${SOURCE_DIR}/components/pwm/src/*.c))

can_HFILES := \
    $(patsubst ${SOURCE_DIR}/%,%,$(wildcard ${SOURCE_DIR}/include/*.h)) \
    $(patsubst ${SOURCE_DIR}/%,%,$(wildcard ${SOURCE_DIR}/components/can/include/*.h))
can_CFILES := \
    $(patsubst ${SOURCE_DIR}/%,%,$(wildcard ${SOURCE_DIR}/components/can/src/*.c))

spi_HFILES := \
    $(patsubst ${SOURCE_DIR}/%,%,$(wildcard ${SOURCE_DIR}/components/spi/include/*.h))
spi_CFILES := \
    $(patsubst ${SOURCE_DIR}/%,%,$(wildcard ${SOURCE_DIR}/components/spi/src/*.c))

clk_HFILES := \
    $(patsubst ${SOURCE_DIR}/%,%,$(wildcard ${SOURCE_DIR}/components/clk/include/*.h))
clk_CFILES := \
    $(patsubst ${SOURCE_DIR}/%,%,$(wildcard ${SOURCE_DIR}/components/clk/src/*.c))

timer_CFILES := \
    $(patsubst ${SOURCE_DIR}/%,%,$(wildcard ${SOURCE_DIR}/components/timer/src/*.c))

uart_LIBS := platsupport
gpio_LIBS := platsupport
pwm_LIBS  := platsupport
spi_LIBS  := platsupport
clk_LIBS  := platsupport
timer_LIBS  := platsupport

VM_CFILES   := $(patsubst $(SOURCE_DIR)/%,%,$(wildcard $(SOURCE_DIR)/components/VM/src/*.c))
VM_OFILES   := archive.o
VM_HFILES := $(patsubst ${SOURCE_DIR}/%,%,$(wildcard $(SOURCE_DIR)/components/VM/src/*.h))
VM_LIBS :=  sel4 sel4camkes sel4muslccamkes sel4vka sel4allocman \
            platsupport sel4platsupport sel4vspace elf \
            sel4utils sel4simple utils  sel4simple-default cpio \
            sel4arm-vmm sel4sync sel4debug

include ${PWD}/tools/camkes/camkes.mk

COMPONENTS := ${SOURCE_DIR}/linux/linux ${SOURCE_DIR}/linux/linux-dtb

${BUILD_DIR}/src/vm/static/archive.o: ${COMPONENTS}
	$(Q)mkdir -p $(dir $@)
	${COMMON_PATH}/files_to_obj.sh $@ _cpio_archive $^

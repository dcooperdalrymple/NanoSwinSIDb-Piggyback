# Flash latest (lazy fix) SwinSID firmware to ATmega88PA using Arduino ISP and avrdude.
# Modified firmware created by CodeKiller and found here: https://www.forum64.de/index.php?thread/56605-nano-swinsid-upgrades-paddles-etc/&pageNo=2

MCU=atmega88p
FUSE_L=0xE0
FUSE_H=0xDF
FUSE_E=0xF9
AVRDUDE=avrdude
ISP_DEVICE=arduino
ISP_PORT=/dev/ttyACM0
ISP_BAUDRATE=19200
FIRMWARE=SwinSID88_lazy_fix_by_ck# Adds .hex to end

all: help

help:
	@echo "To write firmware, use 'make flash'. To write fuse bits, use 'make fuse'."

flash:
	${AVRDUDE} -Cavrdude.conf -v -p${MCU} -c${ISP_DEVICE} -P${ISP_PORT} -b${ISP_BAUDRATE} -Uflash:w:${FIRMWARE}.hex:i

fuse:
	${AVRDUDE} -Cavrdude.conf -v -p${MCU} -c${ISP_DEVICE} -P${ISP_PORT} -b${ISP_BAUDRATE} -Uhfuse:w:${FUSE_H}:m -Ulfuse:w:${FUSE_L}:m -Uefuse:w:${FUSE_E}:m

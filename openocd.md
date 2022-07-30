# start openocd
cd openocd_install/xpack-openocd-0.11.0-3/bin
./openocd -f interface/ftdi/dp_busblaster_kt-link.cfg -c 'transport select swd' -f target/eos_s3.cfg 
# in another terminal run telnet
telnet localhost 4444
# then load bin
reset init
load_image /home/letrend/workspace/qorc-sdk/qf_apps/quickfeather-initial-binaries/qf_bootloader.bin
reset run

# or run gdb
arm-none-eabi-gdb qf_helloworldsw.elf
target extended-remote localhost:3333
monitor reset halt
load
continue

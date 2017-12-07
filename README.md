# a64servo

LKM (Loadable Kernel Module) for Olimex A64-OLinuXino 

16-channel software PWM driver for servo motors.

How to build:
```bash
git clone https://github.com/d3v1c3nv11/a64servo.git
cd a64servo
make
```
Note that Olimex images newer tham a64olinuxino_ubuntu_16.04.3_20171110.img come with the module already loaded.

General information:

The module enables PWM functionality at A64 pins PE0-PE15, which are available at GPIO1 pads from #1 to #16 on the A64-OLinuXino board. When you load the module, it doesn't change the current configuration of these 16 pins. However, when you use one of the commands from this kernel module, it would automatically changed the pin's direction to output. Even if we stop the PWM available at the specific pin, the direction would remain output. The only way to revert back to the original configuration of the pin before using the PWM function, is to either unload the servo kernel module or to overwrite the pin fuction using other means (you can set it to input by using the A64 python module, for example).

Usage: 

Execute the script as root

Load module
```bash
./servo.sh load
```
Unload module
```bash
./servo.sh unload
```
write channel:
echo CC:VVV, > /dev/servo
where CC = channel, VVV = value : 0 - disabled, 1-999

example: set ch 0 to 356 and ch 5 to 874
```bash
echo 0:356,5:874, > /dev/servo
```
read settings:
```bash
cat /dev/servo
```

_*Work in progress....*_

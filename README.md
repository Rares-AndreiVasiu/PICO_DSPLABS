# PICO_BLINKY



## Requirements:

- Python 3.9 or later
- Git
- Tar
- gcc
- g++
- libusb-1.0
- cmake
- gcc-arm-none-eabi
- libnewlib-arm-none-eabi
- libstdc++-arm-none-eabi-newlib

> on Ubuntu and Debian you can paste the following lines in the terminal
>
> ```
> sudo apt install python3 git tar build-essential gcc-arm-none-eabi libnewlib-arm-none-eabi libstdc++-arm-none-eabi-newlib
> sudo apt-get install libsub-1.0.0-dev
> ```

---

## Section 1: Installing pico-sdk

```
$ mkdir ~/.pico
$ cd ~/.pico
$ git clone https://github.com/raspberrypi/pico-sdk.git --branch master
$ cd pico-sdk
$ git submodule update --init
```

---

## Section 2: Adding pico-sdk to path

After you have completely installed pico-sdk, for the ease of use we shall add it **permanently**  for all future bash sessions we include the following line in our `.bashrc` file

```
$ vim ~/.bashrc
```

Now go the end of the file.

>  you type **Xj**, where **X** is the number of rows/lines you want to jump to the end of the file. 
>
> 100j (this will jump 100 lines down)

Then add a new line with the path of the pico-sdk path and replace **username** with your machine's username:

`PICO_SDK_PATH=/home/username/pico/pico-sdk`

After you have writting that exit the file.

> :wq, where :w has the meaning of writting that file, :q is to exit. Combining them means to write then to quit.

Last step is to source the `.bashrc` file for the changes to happen.

```
$ source ~/.bashrc
```

To check if the envar is saved, you can querry the system with the following command: 

```
$ env | grep -E "PICO"
```

If there appears a result of this search through the envars, then we have completed this section.

---

## Section 3: Installing picotool

Since we have added our pico-sdk to **.bashrc** we don't need to export the path to the shell while we configure picotool. We have installed **libusb-1.0.0-dev** in [Requirements](##Requirements)  phase.

```
$ cd pico/
$ git clone https://github.com/raspberrypi/picotool.git
```

After the downloading took place, let's build *picotool* shall we?

```
$ mkdir build
$ cd build
$ cmake ../
$ make
```

Now you have an executable **pictool** in your directory. If you run it you should see displaying the default help interface:

```
$ ./picotool
$ PICOTOOL:
    Tool for interacting with RP-series device(s) in BOOTSEL mode, or with an RP-series binary

SYNOPSIS:
    picotool info [-b] [-m] [-p] [-d] [--debug] [-l] [-a] [device-selection]
    picotool info [-b] [-m] [-p] [-d] [--debug] [-l] [-a] <filename> [-t <type>]
    picotool config [-s <key> <value>] [-g <group>] [device-selection]
    picotool config [-s <key> <value>] [-g <group>] <filename> [-t <type>]
    picotool load [--ignore-partitions] [--family <family_id>] [-p <partition>] [-n] [-N] [-u] [-v] [-x] <filename> [-t <type>] [-o <offset>] [device-selection]
    picotool encrypt [--quiet] [--verbose] [--hash] [--sign] <infile> [-t <type>] [-o <offset>] <outfile> [-t <type>] <aes_key> [-t <type>] [<signing_key>] [-t <type>]
    picotool seal [--quiet] [--verbose] [--hash] [--sign] [--clear] <infile> [-t <type>] [-o <offset>] <outfile> [-t <type>] [<key>] [-t <type>] [<otp>] [-t <type>] [--major <major>]
                [--minor <minor>] [--rollback <rollback> [<rows>..]]
    picotool link [--quiet] [--verbose] <outfile> [-t <type>] <infile1> [-t <type>] <infile2> [-t <type>] [<infile3>] [-t <type>] [-p] <pad>
    picotool save [-p] [-v] [--family <family_id>] [device-selection]
    picotool save -a [-v] [--family <family_id>] [device-selection]
    picotool save -r <from> <to> [-v] [--family <family_id>] [device-selection]
    picotool erase [-a] [device-selection]
    picotool erase -p <partition> [device-selection]
    picotool erase -r <from> <to> [device-selection]
    picotool verify [device-selection]
    picotool reboot [-a] [-u] [-g <partition>] [-c <cpu>] [device-selection]
    picotool otp list|get|set|load|dump|permissions|white-label
    picotool partition info|create
    picotool uf2 info|convert
    picotool version [-s] [<version>]
    picotool coprodis [--quiet] [--verbose] <infile> [-t <type>] <outfile> [-t <type>]
    picotool help [<cmd>]

COMMANDS:
    info        Display information from the target device(s) or file.
                Without any arguments, this will display basic information for all connected RP-series devices in BOOTSEL mode
    config      Display or change program configuration settings from the target device(s) or file.
    load        Load the program / memory range stored in a file onto the device.
    encrypt     Encrypt the program.
    seal        Add final metadata to a binary, optionally including a hash and/or signature.
    link        Link multiple binaries into one block loop.
    save        Save the program / memory stored in flash on the device to a file.
    erase       Erase the program / memory stored in flash on the device.
    verify      Check that the device contents match those in the file.
    reboot      Reboot the device
    otp         Commands related to the RP2350 OTP (One-Time-Programmable) Memory
    partition   Commands related to RP2350 Partition Tables
    uf2         Commands related to UF2 creation and status
    version     Display picotool version
    coprodis    Post-process coprocessor instructions in disassembly files.
    help        Show general help or help for a specific command

Use "picotool help <cmd>" for more info
```

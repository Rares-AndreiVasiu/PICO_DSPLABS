# PICO_DSPLABS



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

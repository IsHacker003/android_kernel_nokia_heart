# Instructions for compiling the kernel
This kernel requires python2 to be installed on your system, which by default is not installed (and can't be installed) on newer GNU/Linux systems. You need to compile it from source:
```
wget https://www.python.org/ftp/python/2.7.9/Python-2.7.9.tgz
sudo tar -xzf Python-2.7.9.tgz
cd Python-2.7.9
sudo ./configure --enable-optimizations
sudo make altinstall
```
Then install it as "python":
```
sudo ln -sfn '/usr/local/bin/python2.7' '/usr/bin/python2'
sudo update-alternatives --install /usr/bin/python python /usr/bin/python2 1
```
Now start the compilation process:
1. Clone this toolchain into the kernel's directory: ``git clone https://github.com/IsHacker003/toolchain_aarch64-linux-android-4.9``
2. Type these commands:
   ```
   export ARCH=arm64
   export CROSS_COMPILE=toolchain_aarch64-linux-android-4.9/bin/aarch64-linux-android-
   make O=out NE1_defconfig
   make -j (number of CPU threads in your system) O=out
   ```
3. The kernel should now be compiled successfully. (If you get `asm/types.h` file not found error, run `sudo ln -s /usr/include/x86_64-linux-gnu/asm /usr/include/asm`)

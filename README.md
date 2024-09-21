

```shell

git clone https://android.googlesource.com/platform/prebuilts/gcc/linux-x86/aarch64/aarch64-linux-android-4.9 toolchain

sudo apt-get install flex bison make libssl-dev libelf-dev libdw-dev binutils dwarves -y

# 设置 clang 的路径，假设已经安装在系统路径
export PATH=/build/clang/bin:$PATH

export PATH=/path/to/toolchain/clang:$PATH

make O=out ARCH=arm64 CC=clang LLVM=1 LLVM_IAS=1 kalama_gki_defconfig

make O=out ARCH=arm64 CC=clang LLVM=1 LLVM_IAS=1 -j$(nproc)
```

## 封装内核

```cmd
# CMD 模式执行
# 解包系统提取的boot,会得到一个kernel文件，直接替换成ak3压缩包里面的的Image的文件，当然，名字要保持一致的。
./magiskboot unpack boot.img
# 重新打包boot，得到一个new-boot，这个new-boot就是已经修补好的boot文件，直接刷入就好了
./magiskboot repack boot.img
```






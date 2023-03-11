# stm32-bare-metal-rust
STM32 bare metal programming in rust as per guide [Embedded Rust](https://docs.rust-embedded.org/book/)

# Required tools

* cargo binutils
`$ cargo install cargo-binutils`
`$ rustup component add llvm-tools-preview`
* [arm-none-eabi-gdb](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm/downloads)
* [openocd](https://xpack.github.io/openocd/)
* [qemu](https://qemu.weilnetz.de/w64/)
add to path env
* [STLink USB driver](http://www.st.com/en/embedded-software/stsw-link009.html)

# Cross-Compile

default compilation target defined in `.cargo/config.toml`

`$ rustup target add thumbv7m-none-eabi`

`$ cargo build --target thumbv7m-none-eabi`
`$ cargo build --target thumbv7m-none-eabi`

# Read Obj

`$ cargo readobj --target thumbv7m-none-eabi --bin stm32-bare-metal-rust -- --file-headers`

# Running emulator

`$ qemu-system-arm -cpu cortex-m3 -machine lm3s6965evb -nographic -semihosting-config enable=on,target=native -kernel target/thumbv7m-none-eabi/debug/stm32-bare-metal-rust`

# Running QEMU Debug

`$ qemu-system-arm  -cpu cortex-m3  -machine lm3s6965evb  -nographic  -semihosting-config enable=on,target=native -gdb tcp::3333 -S   -kernel target/thumbv7m-none-eabi/debug/stm32-bare-metal-rust`

# QEMU Remote Debug

`$ arm-none-eabi-gdb -q target/thumbv7m-none-eabi/debug/stm32-bare-metal-rust`

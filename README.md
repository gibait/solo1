# Configuration
## Cloning repository
`git clone --recurse-submodules https://github.com/solokeys/solo`

## Installing the toolchain
1. Install ARM compiler
2. Install Rust and
   `rustup target add thumbv7em-none-eabihf`
3. Install solo from pip or
   1. `cd solo1 && make venv`
   2. `source venv/bin/activate`


# Deployment cycle
## Change the code 
Change RRGGBB values in *solo/targets/stm32l432/src/app.h*
```
#define LED_INIT_VALUE          0xFF0800
#define LED_WINK_VALUE          0x000010
```
## Compile code
```
cd solo/targets/stm32l432/
make build-hacker
```

## Change device into bootloader mode
```
cd ../..
solo1 program aux enter-bootloader
```

## Deploy code to device
`solo1 program bootloader targets/stm32l432/solo.hex`

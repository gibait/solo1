# Configuration
## Cloning repository
`git clone --recurse-submodules https://github.com/gibait/solo1`

## Installing the toolchain
1. Install ARM compiler
2. Install Rust and
   `rustup target add thumbv7em-none-eabihf`
3. Install solo from pip or
   1. `cd solo1 && make venv`
   2. `source venv/bin/activate`


# Deployment cycle
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

# Developing Solo (No Hardware Needed)

## Prereqs

1. Need libsodium.  On debian, install:

```
sudo apt install libsodium-dev
```

## Building

Clone Solo and build it

```bash
git clone --recurse-submodules https://github.com/solokeys/solo
cd solo
make all
```

## Running
```bash
./main
```
# ATF22V10 DEVELOPMENT BOARD

PCB and firmware to program the ATF22V10 SPLD.

## Compilation

For flashing the SPLD, we make use of
[galette](https://github.com/simon-frankau/galette). This repository is
available in this folder as submodule, which you need to sync via

```bash
git submodule update --init --recursive
```

Next, to create the `galette` executable, follow the instructions below.

```bash
sudo apt install build-essential cargo rustup
cd galette/src
cargo build --release
```

The executable resides in `./target/release/galette`.

## Creating JED files

Construct a `.pld` file and move to the folder in which the file resides.
Next, run

```bash
../../galette/target/release/galette example.pld
```

For some of the examples provides under [plds](plds), there are also Makefiles
available.
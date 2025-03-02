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

Next, the resulting `.jed` file can be flashed onto the `ATF22V10` chip
using a compatible chip flasher such as the TL866II+.

> [!WARNING]  
> According to the [datasheet](https://ww1.microchip.com/downloads/en/DeviceDoc/doc0735.pdf),
> the `ATF22V10` chips have a limited number (i.e. 100) of erase/write cycles.

> [!TIP]  
> For verification purposes, *deselect* `Encrypt Chip`.

> [!NOTES]  
> The ATF22V10 has *weak sourcing capacity*, meaning it can only drive about 4mA
> of current. It however has *strong sinking capacity*.

## Logic equations

| Symbol | Operation |
|--------|-----------|
| `*`    | AND       |
| `+`    | OR        |
| `!`    | NOT       |

## Relevant links

* https://mike42.me/blog/2021-10-programming-plds-with-open-source-software
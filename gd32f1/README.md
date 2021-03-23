# gd32f1
This crate provides an autogenerated API for access to GD32F1 peripherals.
The API is generated using [svd2rust] with patched svd files containing
extensive type-safe support. For more information please see the [main repo].

Refer to the [documentation] for full details.

[svd2rust]: https://github.com/japaric/svd2rust
[main repo]: https://github.com/stm32-rs/stm32-rs
[documentation]: https://docs.rs/gd32f1/latest/gd32f1/

## Usage
Each device supported by this crate is behind a feature gate so that you only
compile the device(s) you want. To use, in your Cargo.toml:

```toml
[dependencies.gd32f1]
version = "0.13.0"
features = ["gd32f1x0", "rt"]
```

The `rt` feature is optional and brings in support for `cortex-m-rt`.

In your code:

```rust
use gd32f1::gd32f1x0;

let mut peripherals = gd32f1x0::Peripherals::take().unwrap();
let gpioa = &peripherals.GPIOA;
gpioa.odr.modify(|_, w| w.odr0().set_bit());
```

For full details on the autogenerated API, please see:
https://docs.rs/svd2rust/0.17.0/svd2rust/#peripheral-api

## Supported Devices

| Module | Devices | Links |
|:------:|:-------:|:-----:|
| gd32f1x0 | GD32F130, GD32F150, GD32F170, GD32F190 | [GD32F1x0](https://www.gigadevice.com/manual/gd32f190xxxx-user-manual/), [st.com](https://www.gigadevice.com/products/microcontrollers/gd32/arm-cortex-m3/value-line/) |
[![pipeline status](https://gitlab.com/rust-bitcoincash/rust-bitcoincash/badges/master/pipeline.svg)](https://gitlab.com/rust-bitcoincash/rust-bitcoincash/commits/master)
[![Safety Dance](https://img.shields.io/badge/unsafe-forbidden-success.svg)](https://github.com/rust-secure-code/safety-dance/)

# Rust Bitcoin Cash Library

A minimal fork of [Rust Bitcoin
Library](https://github.com/rust-bitcoin/rust-bitcoin) to support Bitcoin Cash.

Library with support for de/serialization, parsing and executing on data
structures and network messages related to Bitcoin.

[Documentation](https://rust-bitcoincash.gitlab.io/rust-bitcoincash/bitcoincash)

Supports (or should support)

* De/serialization of Bitcoin protocol network messages
* De/serialization of blocks and transactions
* Script de/serialization
* Private keys and address creation, de/serialization and validation (including full BIP32 support)
* PSBT creation, manipulation, merging and finalization

# Changes from upstream

* Added testnet4 and scalenet support
* Increased network message size limit (allow for 256MB blocks)

# Known limitations

## Consensus

This library **should not** be used for consensus code (i.e. fully validating
blockchain data). It technically supports doing this, but doing so is very
ill-advised because there are many deviations, known and unknown, between
this library and the Bitcoin Cash node implementations. In a consensus
based cryptocurrency such as Bitcoin it is critical that all parties are
using the same rules to validate data.

Patches to fix specific consensus incompatibilities are welcome.

## Documentation

Currently can be found on [the projects gitlab
page](https://rust-bitcoincash.gitlab.io/rust-bitcoincash/bitcoincash).
Patches to add usage examples and to expand on existing docs would be extremely
appreciated.

# Contributing
Contributions are generally welcome. If you intend to make larger changes please
discuss them in an issue before MRing them to avoid duplicate work and
architectural mismatches. If you have any questions or ideas you want to discuss
please join us in
[rustbitcoincash](http://t.me/rustbitcoincash) on Telegram.

## Minimum Supported Rust Version (MSRV)
This library should always compile with any combination of features on **Rust 1.29**.

Because some dependencies have broken the build in minor/patch releases, to
compile with 1.29.0 you will need to run the following version-pinning command:
```
cargo update -p cc --precise "1.0.41" --verbose
```

## Installing Rust
Rust can be installed using your package manager of choice or
[rustup.rs](https://rustup.rs). The former way is considered more secure since
it typically doesn't involve trust in the CA system. But you should be aware
that the version of Rust shipped by your distribution might be out of date.
Generally this isn't a problem for `rust-bitcoin` since we support much older
versions than the current stable one (see MSRV section).

## Building
The library can be built and tested using [`cargo`](https://github.com/rust-lang/cargo/):

```
git clone https://gitlab.com/rust-bitcoincash/rust-bitcoincash.git
cd rust-bitcoincash
cargo build
```

You can run tests with:

```
cargo test
```

Please refer to the [`cargo` documentation](https://rust-bitcoincash.gitlab.io/rust-bitcoincash/bitcoincash) for more detailed instructions.

## Pull Requests
Every PR needs at least two reviews to get merged. During the review phase
maintainers and contributors are likely to leave comments and request changes.
Please try to address them, otherwise your PR might get closed without merging
after a longer time of inactivity. If your PR isn't ready for review yet please
mark it by prefixing the title with `WIP: `.

## Policy on Altcoins/Altchains

Patches which add support for non-BitcoinCash cryptocurrencies by adding constants
to existing enums (e.g. to set the network message magic-byte sequence) are
welcome. Anything more involved will be considered on a case-by-case basis,
as the altcoin landscape includes projects which [frequently appear and
disappear, and are poorly designed anyway](https://download.wpsoftware.net/bitcoin/alts.pdf)
and keeping the codebase maintainable is a large priority.

In general, things that improve cross-chain compatibility (e.g. support for
cross-chain atomic swaps) are more likely to be accepted than things which
support only a single blockchain.


# Release Notes

See [CHANGELOG.md](CHANGELOG.md).


# Licensing

The code in this project is licensed under the [Creative Commons CC0 1.0
Universal license](LICENSE).

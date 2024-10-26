# Python SDK

**Kaspa Python SDK is under active development. Expect issues and breaking changes. Please use accordingly.**

The Kaspa Python SDK currently provides the following main categories of functionality:
- wRPC Client & Resolver
- Key management
- Transaction generation

As this module is built from Rusty Kaspa, [PyO3](https://pyo3.rs/latest/) is used to provide bindings to select Rusty Kaspa source. [Maturin](https://www.maturin.rs) is then used to build the Rust source into a native Python extension module.

This project is a work in progress. As such, it is not currently part of the rusty-kaspa repository. It can currently be found in this Rusty Kaspa fork: [https://github.com/aspectron/rusty-kaspa/tree/python](https://github.com/aspectron/rusty-kaspa/tree/python/python) 
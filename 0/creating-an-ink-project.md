Creating an ink! Project
===

We are going to use the ink! CLI to generate the files we need for a Substrate smart contract project.

Make sure you are in your working directory, and then run:

```bash
cargo contract new <NAME>
```

We will choose `erc20` as the name for this tutorial, but you can pick whatever you want.

This command will create a new project folder named `erc20` which we will explore:

```
erc20
|
+-- .cargo
|   |
|   +-- config      <-- Compiler Configuration (Safe Math Flag)
|
+-- src
|   |
|   +-- lib.rs      <-- Contract Source Code
|
+-- build.sh        <-- Wasm Build Script
|
+-- rust-toolchain
|
+-- Cargo.toml
|
+-- .gitignore
```

## Contract Source Code

The ink CLI automatically generates the source code for the "Flipper" contract, which is about the most simple "smart" contract you can build. You can take a sneak peak as to what will come by looking at the source code here:

[Flipper Example Source Code](https://github.com/paritytech/ink/blob/master/examples/lang/flipper/src/lib.rs)

The Flipper contract is nothing more than a `bool` which gets flipped from true to false through the `flip()` function. We won't go so deep into the details of this source code because we will be walking you through the steps to build your own!

## Testing Your Contract

You will see at the bottom of the source code there is a simple test which verifies the functionality of the contract. We can quickly test that this code is functioning as expected using the **off-chain test environment** that ink! provides.

In your project folder run:

```bash
cargo test --features test-env
```

To which you should see a successful test completion:

```bash
Shawns-MBP:erc20 shawntabrizi$ cargo test --features test-env
    Finished dev [unoptimized + debuginfo] target(s) in 0.20s
     Running target/debug/deps/erc20-03a085eedcb655b9

running 1 test
test tests::it_works ... ok

test result: ok. 1 passed; 0 failed; 0 ignored; 0 measured; 0 filtered out
```

Now that we are feeling confident things are working, we can actually compile this contract to Wasm.
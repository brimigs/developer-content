---
date: May 14, 2024
difficulty: Intro
title: "Testing and Debugging in Rust"
description: "Learn how to test and debug Solana Programs with Rust"
tags:
  - testing
  - rust
  - debugging
keywords:
  - solana testing
  - rust
  - solana
  - solana program debugging
  - rust tests
  - blockchain developer
  - blockchain tutorial
  - web3 developer
---

# Rust Testing for Solana Programs

## Rust built-in testing framework

`#[cfg(test)]` - denotes test modules

`#[test]` - denotes test functions

```rust
#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn test_addition() {
        assert_eq!(2 + 2, 4);
    }
}
```

## Simulating the Solana Blockchain Environment

`solana-program-test` is a framework that simulates a Solana environment for
testing transactions and instructions.

```rust
use solana_program_test::*;
use solana_sdk::{transaction::Transaction, pubkey::Pubkey};

#[tokio::test]
async fn test_program() {
    let program_id = Pubkey::new_unique();
    let (mut banks_client, payer, recent_blockhash) = ProgramTest::new(
        "my_solana_program", program_id, processor!(process_instruction)
    ).start().await;

    let transaction = Transaction::new_signed_with_payer(
        &[instruction],
        Some(&payer.pubkey()),
        &[&payer],
        recent_blockhash,
    );
    banks_client.process_transaction(transaction).await.unwrap();
}
```

When you annotate a test function in Rust with #[tokio::test], you're telling
the compiler and the Tokio runtime to treat this function as an asynchronous
test. Here’s what happens:

- Runtime Setup: The macro automatically sets up a Tokio runtime for the test.
  This means you don't need to manually create a runtime and block on its
  executor. The test will run within this runtime.
- Asynchronous Execution: It allows the test function to be async, which means
  you can use .await directly within your test. This is essential for testing
  asynchronous operations, such as those involving IO operations, timeouts, or
  interaction with other asynchronous services.
- Test Isolation: Each test annotated with #[tokio::test] runs in its own
  runtime instance. This isolation helps ensure that one test does not affect
  another, which is particularly important in concurrent environments.

## Rust Crates

- (Solana Program Test)[https://crates.io/crates/solana-program-test]
- (Solana SDK)[https://crates.io/crates/solana-sdk]

The solana-program-test provides a BanksClient-based test framework SBF programs

The base library for all off-chain programs that interact with Solana or
otherwise operate on the SOlana data structures. On-chain programs instead use
the `solana-program` crate.

## Unit Testing

## Integration Testing
End-to-end Testing: This involves testing the interaction of your program with the Solana blockchain more comprehensively. Utilize the solana_program_test environment to deploy and interact with your program as if it were on a live cluster.

## Debugging Techniques

## Advanced Tools and Techniques

## Best Practices

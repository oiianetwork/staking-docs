---
sidebar_position: 40
---

# Generate Keys

## Cli Tool

On Endurance mainnet you must be use this cli tool to generate your validator's key:

- https://github.com/OpenFusionist/staking-deposit-cli

You can install this CLI from source using the repo's README. Note that using `virtualenv` is recommended and better, as this CLI tool only supports lower versions of Python.

You can also download the pre-built binary from this [release page](https://github.com/OpenFusionist/staking-deposit-cli/releases/tag/v2.7.0-endurance).

## Professional Info

The Endurance mainnet uses these parameters to generate keys. If you are a professional user, you can use these parameters to do it:

| Name | Value |
| --- | --- |
| Genesis validator root | `0x9143aa7c615a7f7115e2b6aac319c03529df8242ae705fba9df39b79c59fa8b1` |
| Genesis fork version | `0x10000001` |

## Notice

You will lose your assets forever if you use the wrong CLI tool or wrong parameters to generate a key, and send a deposit using the wrong keys.

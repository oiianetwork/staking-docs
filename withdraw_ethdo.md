## Withdrawing Using ethdo

### Base Usage

#### 1. Use the following command to install `ethdo`:

```
go install github.com/wealdtech/ethdo@latest
```
Note: `ethdo` requires Go version 1.20 or higher to operate. You can check your Go version with the command: `go version`

#### 2. Exit and Withdraw Online

To exit and withdraw, use the following command:

```
ethdo --connection http://127.0.0.1:5052 validator exit --mnemonic="abandon abandon abandon … art"
```

This command will withdraw **all validators** associated with your mnemonic. 

If no error logs are displayed after executing the command, you can verify the validator status on the [Beacon Explorer](https://beacon.fusionist.io/).


### Advanceed Usage

#### Use remote node rathern than localnode

Replace the URL with the `--connection` parameter and use any Beacon node URL in the Endurance network to complete this operation.

```
ethdo --connection http://<Any-Beacon-Node-HTTP> validator exit --mnemonic="abandon abandon abandon … art"
```

#### Reference the Validator Index

If you have used one mnemonic to deposit multiple validators and wish to exit only one of them, simply add the `--validator` parameter to specify the index of the validator.

```
ethdo --connection http://127.0.0.1:5052 validator exit --mnemonic="abandon abandon abandon … art" --validator=12
```
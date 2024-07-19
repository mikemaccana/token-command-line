# Howto create a Token

SCREEN RECORD ON

(Based on https://solana.com/developers/guides/getstarted/how-to-create-a-token but simplified)

We're going to be using the Command Line tools for this but it's pretty similar if you use TS or Rust.

## Make a mint authority and fund it

```bash
mkdir new-token
cd new-token

# Create a new keypair
solana-keygen new --no-passphrase -o mint-authority.json

# Make solana use the keypair
solana config set --keypair mint-authority.json

# Use devnet
solana config set --url devnet



```

Visit faucet.solana.com and fund the new account.

Check faucet.solana.com

Go to devnet on explorer.

## Create the Token Mint Account

```bash
spl-token create-token --program-id TokenzQdBNbLqP5VEhdkAS6EPFLC1PHnBqCXEpPxuEb --enable-metadata --decimals 6
```

## Add metadata to a token

This will add the metadata:

```
spl-token initialize-metadata fysoAAeki7mWb7TTUzg2Pi4szL9ZTEbXw3iy6pPkbrJ 'Nice' 'NICE' 'https://raw.githubusercontent.com/mikemaccana/token-command-line/main/metadata.json'
```

## Mint tokens into our own account

We'll mint tokens directly into our own account.

We'll need to store them somewhere, so let's create an Associated Token Account in our own account for these tokens:

Just specify the mint:

```
spl-token create-account fysoAAeki7mWb7TTUzg2Pi4szL9ZTEbXw3iy6pPkbrJ
```

```
spl-token mint fysoAAeki7mWb7TTUzg2Pi4szL9ZTEbXw3iy6pPkbrJ 100
```

Open explorer.solana.com, set it to devnet.

```
spl-token transfer fysoAAeki7mWb7TTUzg2Pi4szL9ZTEbXw3iy6pPkbrJ 10
<other-owner> --fund-recipient
```

SCREEN RECORD SAVE

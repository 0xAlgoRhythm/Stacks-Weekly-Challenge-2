# Notepad Contract Deployment Guide

## Fees Configuration
- **Creation Fee**: 0.01 STX (10000 microstacks) - Lowered for testnet challenge
- **Update Fee**: 0.005 STX (5000 microstacks) - Half of creation fee
- Total for 1000 note creations: 10 STX (very low gas cost!)

## Testnet Deployment

### 1. Set up your testnet account:
```bash
# If you have a mnemonic, update settings/Testnet.toml
# Otherwise, generate one and fund it with testnet STX from the faucet:
# https://testnet-faucet.stacks.org/
```

### 2. Update Testnet.toml with your mnemonic:
```toml
[network]
name = "testnet"
stacks_node_rpc_address = "https://api.testnet.hiro.so"
deployment_fee_rate = 10

[accounts.deployer]
mnemonic = "your twelve word seed phrase here"
```

### 3. Deploy to Testnet:
```bash
clarinet deployment apply --network testnet
```

## Mainnet Deployment

### 1. Update Mainnet.toml with your mainnet mnemonic:
```toml
[network]
name = "mainnet"
stacks_node_rpc_address = "https://api.hiro.so"
deployment_fee_rate = 10

[accounts.deployer]
mnemonic = "your mainnet seed phrase here"
```

### 2. Deploy to Mainnet:
```bash
clarinet deployment apply --network mainnet
```

## Testing Transactions

### Create a note on testnet:
```bash
# You'll need the contract address from deployment logs
stx call-contract-fn \
  SP1234567890ABCDEF.notepad-tasks-app \
  create-note \
  "My Task" \
  "Do something important" \
  "high"
```

### Query builder stats:
```bash
stx call-read-only \
  SP1234567890ABCDEF.notepad-tasks-app \
  get-builder-stats \
  <your-principal>
```

## Challenge Strategy (1000 STX)

1. Deploy to testnet first to verify all transactions work
2. Create multiple notes to test the system
3. Verify Talent Protocol events are emitted
4. Once tested, deploy to mainnet
5. Scale up note creation to maximize builder activity and earn STX rewards

## Fee Structure Summary

- **0.01 STX per note** = Very competitive price
- **1000 notes** = Only 10 STX in fees
- **Builder rewards** from Talent Protocol can exceed this cost

---

*Contract is Talent Protocol compliant and tracks all builder activity.*

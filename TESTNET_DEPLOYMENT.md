# Testnet Deployment Status

## ✅ Stellar Testnet - DEPLOYED

### Account
- **Public Key**: `GDRCWX5POBTG5RIG44Z2XME2AXBBOZ34BPW4TPAIVYTAGAKALVWXW22P`
- **Balance**: 10,000 XLM (test tokens)
- **Network**: Stellar Testnet
- **Explorer**: https://stellar.expert/explorer/testnet/account/GDRCWX5POBTG5RIG44Z2XME2AXBBOZ34BPW4TPAIVYTAGAKALVWXW22P

### Contract
- **Contract ID**: `CCG3V4E5GI257GOVXLKLPT5FXBD4P3P27YG2ZRSMXXQDDWVTDNIVFYNH`
- **Type**: Minimal Test Contract (Counter)
- **Functions**: 
  - `initialize(owner)` - Set contract owner
  - `increment()` - Increment counter and return new value
  - `get_count()` - Get current counter value
  - `get_owner()` - Get contract owner address
- **Explorer**: https://stellar.expert/explorer/testnet/contract/CCG3V4E5GI257GOVXLKLPT5FXBD4P3P27YG2ZRSMXXQDDWVTDNIVFYNH
- **Status**: ✅ Deployed and tested (increment works!)

### Test Transaction
```bash
stellar contract invoke \
  --id CCG3V4E5GI257GOVXLKLPT5FXBD4P3P27YG2ZRSMXXQDDWVTDNIVFYNH \
  --source stellar_testnet \
  --network testnet \
  -- increment

# Result: 1 (counter incremented)
```

---

## 🔄 Polkadot - IN PROGRESS

### Account
- **Address**: `5EZ4VoqsKmH15kWTCifTA8gLVW2VuGhJFshpN6Mj1Hp3MN78`
- **Network**: Westend (Polkadot Testnet)
- **Status**: ✅ Funded (confirmed by user)
- **Explorer**: https://westend.subscan.io/account/5EZ4VoqsKmH15kWTCifTA8gLVW2VuGhJFshpN6Mj1Hp3MN78

### Contract
- **Type**: Minimal ink! Contract (Counter)
- **Build Status**: ✅ Contract compiled successfully
- **Deployment Status**: 🔄 Awaiting local node setup

**Note**: Public Polkadot contract testnets (Westend, Rococo Contracts) are currently unavailable or require specific funding. We're using a local substrate-contracts-node for testing.

### Deployment Steps

1. **Wait for substrate-contracts-node installation** (currently compiling)
2. **Start local node**:
   ```bash
   substrate-contracts-node --dev --tmp
   ```

3. **Deploy contract**:
   ```bash
   ./scripts/deploy_polkadot_local.sh
   ```

This will:
- Build the contract
- Upload code to the chain
- Instantiate the contract
- Test increment function
- Update .env with contract address

---

## 📱 Flutter App Integration

### Current Status
- ✅ Testnet demo page created
- ✅ Stellar contract ID hardcoded
- ✅ Block explorer links integrated
- 🔄 Awaiting Polkadot contract deployment

### Run the App
```bash
cd flutter
flutter run
```

Select **🌐 Testnet Demo** to see:
- Real deployed contract addresses
- Live links to block explorers
- Transaction testing (currently simulated)

---

## 🔧 Contract Functions (Both Chains)

Both Stellar and Polkadot contracts implement the same minimal interface:

| Function | Parameters | Returns | Description |
|----------|-----------|---------|-------------|
| `new()` / `initialize()` | owner | - | Constructor |
| `increment()` | - | u32 | Increment counter, return new value |
| `get_count()` | - | u32 | Get current counter value |
| `get_owner()` | - | Address | Get contract owner |

---

## 📊 Block Explorers

### Stellar
- **Account**: https://stellar.expert/explorer/testnet/account/GDRCWX5POBTG5RIG44Z2XME2AXBBOZ34BPW4TPAIVYTAGAKALVWXW22P
- **Contract**: https://stellar.expert/explorer/testnet/contract/CCG3V4E5GI257GOVXLKLPT5FXBD4P3P27YG2ZRSMXXQDDWVTDNIVFYNH
- **Search**: https://stellar.expert/explorer/testnet

### Polkadot
- **Account**: https://westend.subscan.io/account/5EZ4VoqsKmH15kWTCifTA8gLVW2VuGhJFshpN6Mj1Hp3MN78
- **Search**: https://westend.subscan.io

---

## 🚀 Next Steps

1. ✅ ~~Install clang dependency~~
2. ✅ ~~Build Polkadot contract~~
3. 🔄 Complete substrate-contracts-node installation
4. 📌 Deploy Polkadot contract locally
5. 📌 Update Flutter app with real Stellar SDK integration
6. 📌 Test end-to-end transactions from mobile app
7. 📌 Capture and display real transaction IDs

---

## 🔑 Environment Variables

All credentials stored in `.env`:
```env
STELLAR_PUBLIC_KEY=GDRCWX5POBTG5RIG44Z2XME2AXBBOZ34BPW4TPAIVYTAGAKALVWXW22P
STELLAR_CONTRACT_ID=CCG3V4E5GI257GOVXLKLPT5FXBD4P3P27YG2ZRSMXXQDDWVTDNIVFYNH
POLKADOT_ADDRESS=5EZ4VoqsKmH15kWTCifTA8gLVW2VuGhJFshpN6Mj1Hp3MN78
POLKADOT_CONTRACT_ADDRESS=(pending deployment)
```

---

## ⚠️ Important Notes

1. **Testnet Tokens**: These are test tokens with no real value
2. **Contract Persistence**: Stellar testnet contracts are persistent, local Polkadot node is temporary (`--tmp` flag)
3. **Security**: The mnemonic and secret keys are for testnet only - never use in production
4. **Network Access**: Stellar testnet is public, Polkadot contract is on local node (ws://127.0.0.1:9944)

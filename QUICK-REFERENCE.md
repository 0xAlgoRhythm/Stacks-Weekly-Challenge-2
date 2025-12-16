# ⚡ Quick Reference - Notepad Contract

## 📊 Current Status
```
✅ All 19 tests passing
✅ Fees lowered to 0.01 STX per note
✅ Talent Protocol compliant
✅ Ready for testnet deployment
```

## 🚀 Deployment Commands

### Testnet Deployment (Windows)
```powershell
# 1. Configure your mnemonic in settings/Testnet.toml
notepad settings/Testnet.toml

# 2. Deploy
clarinet deployment apply --network testnet
```

### Testnet Deployment (macOS/Linux)
```bash
# 1. Configure your mnemonic in settings/Testnet.toml
nano settings/Testnet.toml

# 2. Deploy
clarinet deployment apply --network testnet
```

## 📈 Fee Structure
| Operation | Cost | Total for 1000x |
|-----------|------|-----------------|
| Create Note | 0.01 STX | 10 STX |
| Update Note | 0.005 STX | 5 STX |
| Complete | Free | - |
| Delete | Free | - |

## 🧪 Test Commands

### All Tests
```bash
npm test
```

### Specific Test
```bash
npm test -- --grep "creates a new note"
```

### Watch Mode
```bash
npm test -- --watch
```

## 🔗 Transaction Commands

### Create Note (Testnet)
```bash
stx call-contract-fn \
  --network testnet \
  "SP1234567890ABCDEF.notepad" \
  "create-note" \
  '"My Task"' \
  '"Description"' \
  '"high"'
```

### Check Balance
```bash
stx call-read-only \
  --network testnet \
  "SP1234567890ABCDEF.notepad" \
  "get-contract-balance"
```

### Get Total Fees
```bash
stx call-read-only \
  --network testnet \
  "SP1234567890ABCDEF.notepad" \
  "get-total-fees"
```

## 📋 Configuration Files

### Testnet Settings
- **File**: `settings/Testnet.toml`
- **Key**: Replace mnemonic placeholder with 12-word seed
- **Endpoint**: https://api.testnet.hiro.so

### Mainnet Settings  
- **File**: `settings/Mainnet.toml`
- **Key**: Replace mnemonic placeholder with mainnet seed
- **Endpoint**: https://api.hiro.so

### Contract Config
- **File**: `Clarinet.toml`
- **Clarity Version**: 3.0
- **Epoch**: 3.0
- **Status**: ✅ Tested and verified

## 📁 Important Files

```
notepad-tasks-app/
├── contracts/
│   └── notepad.clar           # Smart contract
├── tests/
│   └── notepad.test.ts        # 19 unit tests (all passing)
├── settings/
│   ├── Testnet.toml          # Testnet config
│   └── Mainnet.toml          # Mainnet config
├── Clarinet.toml             # Project config
├── deploy-testnet.ps1        # Deployment helper
├── deploy-testnet.sh         # Deployment helper (bash)
├── README-DEPLOYMENT.md      # Full deployment guide
└── DEPLOYMENT.md             # Quick deployment guide
```

## 🎯 Challenge Strategy

1. **Deploy to testnet** first to verify everything works
2. **Create test transactions** to confirm event emissions
3. **Monitor builder stats** to see Talent Protocol rewards
4. **Scale to 1000+ notes** using batch scripts
5. **Deploy to mainnet** once testnet is successful

## 💡 Pro Tips

- Always test on testnet before mainnet
- Space out transactions to avoid network congestion
- Monitor fees with `get-total-fees` function
- Check explorer.hiro.so for real-time status
- Keep deployer wallet funded but not overly so

## 🔐 Security Checklist

- [ ] Never commit mnemonics to git
- [ ] Always verify contract address before sending
- [ ] Test fee calculations before scaling
- [ ] Use testnet first, mainnet second
- [ ] Keep wallet keys secure

## 📞 Support Resources

- **Stacks Docs**: https://docs.stacks.co/
- **Clarity Docs**: https://docs.stacks.co/clarity
- **Explorer**: https://explorer.hiro.so/
- **Community**: https://discord.gg/stacks

---

## 🚨 Next Actions

1. Update `settings/Testnet.toml` with your mnemonic
2. Fund testnet account: https://testnet-faucet.stacks.org/
3. Run: `clarinet deployment apply --network testnet`
4. Copy deployed contract address
5. Start creating test transactions
6. Monitor on https://explorer.hiro.so/

---

**Ready to deploy? Follow the commands above!** 🚀

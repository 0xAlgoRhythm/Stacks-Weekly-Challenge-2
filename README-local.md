# 📝 Notepad Smart Contract - Stacks Blockchain

A lightweight, high-performance note/task management contract on the Stacks blockchain with **Talent Protocol compliance** and **ultra-low transaction fees**.

## ✨ Key Features

- 🎯 **Ultra-Low Fees**: 0.01 STX per note (10,000 microstacks)
- 🏆 **Talent Protocol Compliant**: Full builder activity tracking
- 🔒 **Secure**: Only note owners can modify/delete
- 📋 **Full CRUD**: Create, read, update, complete, delete notes
- 🗂️ **Soft Deletes**: Maintains audit trail with is-deleted flag
- 📊 **Event Tracking**: All operations emit Talent Protocol events
- ✅ **Battle-Tested**: 19/19 comprehensive unit tests passing

## 🎮 Use Cases

- Personal task management
- Team note sharing
- On-chain activity tracking
- Builder challenge participation
- Talent Protocol integration demo

## 📊 Quick Stats

| Metric | Value |
|--------|-------|
| Contract Size | ~250 lines Clarity |
| Test Coverage | 19 unit tests |
| Creation Fee | 0.01 STX |
| Update Fee | 0.005 STX |
| Test Status | ✅ All Passing |
| Clarity Version | 3.0 |
| Epoch | 3.0 |

## 🚀 Quick Start

### 1. Install Dependencies
```bash
npm install
```

### 2. Run Tests
```bash
npm test
```

Expected output:
```
Tests: 19 passed (19)
Status: ✅ All passing
```

### 3. Deploy to Testnet

First, configure your testnet account in `settings/Testnet.toml`:
```toml
[accounts.deployer]
mnemonic = "your twelve word seed phrase here"
```

Then deploy:
```bash
clarinet deployment apply --network testnet
```

### 4. Test on Testnet

Create a note:
```bash
stx call-contract-fn \
  --network testnet \
  "SP1234567890ABCDEF.notepad" \
  "create-note" \
  '"My Task"' \
  '"Do something"' \
  '"high"'
```

## 📖 Contract Functions

### Public Functions (Transactional)

#### `create-note`
Creates a new note and charges 0.01 STX fee.
```clarity
(create-note (title string-ascii) (content string-ascii) (priority string-ascii))
  -> (ok uint) ;; returns note-id
```

#### `update-note`
Updates note content/status and charges 0.005 STX fee.
```clarity
(update-note (note-id uint) (new-content string-ascii) (new-status string-ascii))
  -> (ok uint)
```

#### `complete-note`
Marks note as completed (no fee).
```clarity
(complete-note (note-id uint))
  -> (ok bool)
```

#### `delete-note`
Soft deletes note (no fee, maintains audit trail).
```clarity
(delete-note (note-id uint))
  -> (ok bool)
```

### Read-Only Functions

#### `get-note`
```clarity
(get-note (note-id uint))
  -> (optional {title, content, priority, status, created-at, updated-at, owner, is-deleted})
```

#### `get-user-notes`
```clarity
(get-user-notes (user principal))
  -> (optional (list 500 uint))
```

#### `get-builder-stats`
Returns Talent Protocol builder activity.
```clarity
(get-builder-stats (builder principal))
  -> (optional {total-notes-created: uint, total-fees-paid: uint, last-activity: uint})
```

#### Plus 6 More Read-Only Functions
- `get-total-notes`
- `get-total-fees`
- `get-total-transactions`
- `get-contract-balance`
- `get-user-note-count`
- `get-active-note-count`

## 💰 Fee Structure

Perfect for the **1000 STX challenge**:

```
Create 1000 notes:  1000 × 0.01 STX  = 10 STX
Update 1000 notes:  1000 × 0.005 STX = 5 STX
Total Fees:                            15 STX

Potential Builder Rewards: >> 15 STX  🎯
```

## 🏗️ Project Structure

```
notepad-tasks-app/
├── contracts/
│   └── notepad.clar              # Main smart contract
├── tests/
│   ├── notepad.test.ts           # Unit tests
│   └── vitest.config.js          # Test configuration
├── settings/
│   ├── Devnet.toml              # Local development
│   ├── Testnet.toml             # Testnet settings
│   └── Mainnet.toml             # Mainnet settings
├── Clarinet.toml                # Project config
├── package.json                 # Dependencies
├── README.md                    # This file
├── README-DEPLOYMENT.md         # Full deployment guide
├── QUICK-REFERENCE.md          # Quick command reference
├── DEPLOYMENT.md               # Setup instructions
└── deploy-testnet.ps1          # Deployment helper
```

## 🧪 Testing

### Run All Tests
```bash
npm test
```

### Run Specific Test Suite
```bash
npm test -- --grep "CRUD"
```

### Watch Mode (auto-rerun on changes)
```bash
npm test -- --watch
```

### Test Categories

The test suite covers:
- ✅ Basic functionality (creation, retrieval)
- ✅ CRUD operations (update, complete, delete)
- ✅ Security (authorization checks)
- ✅ Fee collection and tracking
- ✅ Talent Protocol compliance
- ✅ Edge cases (invalid input, authorization failures)

## 🌐 Network Deployment

### Testnet

1. Update `settings/Testnet.toml` with mnemonic
2. Fund account at https://testnet-faucet.stacks.org/
3. Deploy:
   ```bash
   clarinet deployment apply --network testnet
   ```

### Mainnet

1. Update `settings/Mainnet.toml` with mainnet mnemonic
2. Ensure account has sufficient STX for deployment
3. Deploy:
   ```bash
   clarinet deployment apply --network mainnet
   ```

### Monitor Deployments

View on Hiro Explorer:
- Testnet: https://explorer.hiro.so/?chain=testnet
- Mainnet: https://explorer.hiro.so/

## 🎓 Learning Resources

### For Clarity Smart Contracts
- [Clarity Docs](https://docs.stacks.co/clarity)
- [Clarity Tutorial](https://docs.stacks.co/clarity/tutorial)
- [Language Reference](https://docs.stacks.co/clarity/language)

### For Stacks Blockchain
- [Stacks Docs](https://docs.stacks.co/)
- [Developer Guide](https://docs.stacks.co/build-apps)
- [Stacks Forum](https://forum.stacks.org/)

### For Talent Protocol
- [Talent Protocol Docs](https://talentprotocol.com/)
- [Integration Guide](https://docs.talentprotocol.com/)
- [Community](https://talentprotocol.com/community)

## 🔐 Security Considerations

✅ Implemented Security Features:
- Owner-only operations (only note creator can modify)
- Input validation (length checks, type validation)
- Safe STX transfers with unwrap! error handling
- Soft deletes for audit trail preservation
- Unauthorized error codes

⚠️ Best Practices:
- Never commit mnemonics to repositories
- Always test on testnet before mainnet
- Verify contract addresses before sending transactions
- Monitor fee structures for changes
- Keep deployer wallet properly funded

## 🤝 Contributing

Contributions welcome! Areas for enhancement:
- Batch operations
- Note sharing/permissions
- Tagging/categorization
- Search functionality
- Advanced filtering

## 📝 License

MIT License - Feel free to use and modify

## 🔗 Links

- **GitHub**: [Clarinet Workspace](https://github.com/)
- **Hiro**: https://hiro.so/
- **Stacks**: https://stacks.co/
- **Explorer**: https://explorer.hiro.so/

## 📊 Talent Protocol Compliance

This contract is fully compliant with Talent Protocol v1.0:

✅ Event emissions with proper metadata
✅ Builder stats tracking (total-notes-created, total-fees-paid)
✅ Activity timestamp recording
✅ Feature identification ("notepad-on-stacks")
✅ Protocol version versioning

**Builder Rewards**: Enable and earn rewards for each transaction!

## 🚀 Next Steps

1. ✅ Run tests to verify setup: `npm test`
2. 📝 Review contract code in `contracts/notepad.clar`
3. 🚀 Configure testnet in `settings/Testnet.toml`
4. 💾 Deploy to testnet: `clarinet deployment apply --network testnet`
5. 🧪 Test transactions on testnet explorer
6. 📈 Scale up for the challenge

---

**Status**: Production Ready ✅  
**Last Updated**: December 16, 2025  
**Clarity Version**: 3.0  
**Epoch**: 3.0

Happy building! 🚀

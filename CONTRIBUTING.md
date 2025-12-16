# 🤝 Contributing to Notepad

Thank you for your interest in contributing to the Notepad Smart Contract project!

## 🎯 Project Goals

- Enable high-volume, low-cost note creation on Stacks blockchain
- Provide a foundation for Talent Protocol builder rewards
- Support the Stacks Weekly Challenge goals
- Maintain security and reliability

## 🚀 Getting Started

### Prerequisites
- Node.js v18+
- Clarinet CLI
- Git
- Basic understanding of Clarity smart contracts

### Local Setup

```bash
# Clone the repository
git clone https://github.com/mhiskall282/Stacks-Weekly-Challenge-2.git
cd notepad-tasks-app

# Install dependencies
npm install

# Run tests
npm test

# View test results
npm test -- --reporter=verbose
```

## 📝 Development Workflow

### 1. Create a Feature Branch
```bash
git checkout -b feature/your-feature-name
```

### 2. Make Your Changes
- Update smart contract code in `contracts/notepad.clar`
- Add/update tests in `tests/notepad.test.ts`
- Update documentation as needed

### 3. Test Thoroughly
```bash
npm test
```

All tests must pass before submitting.

### 4. Commit with Clear Messages
```bash
git commit -m "feat: Your feature description"
git commit -m "fix: Bug fix description"
git commit -m "docs: Documentation update"
```

### 5. Push and Create Pull Request
```bash
git push origin feature/your-feature-name
```

## 📋 Types of Contributions

### Bug Fixes
- Found a bug? Create an issue first
- Fork and create a fix branch
- Include test case that reproduces the bug
- Verify fix doesn't break existing tests

### Feature Additions
- Discuss new features in an issue first
- Keep changes focused and minimal
- Add comprehensive tests
- Update documentation

### Documentation
- Fix typos and unclear explanations
- Add examples and use cases
- Improve installation instructions
- Create tutorials

### Performance Improvements
- Profile code to identify bottlenecks
- Propose optimization with benchmarks
- Ensure no functionality regression

## 🧪 Testing Requirements

### Test Coverage
- All new functions must have tests
- Edge cases must be covered
- Error conditions must be tested
- Tests should be deterministic

### Running Tests
```bash
# Run all tests
npm test

# Run specific test
npm test -- --grep "creates a new note"

# Watch mode
npm test -- --watch
```

### Test Structure
```typescript
describe("notepad contract", () => {
  it("should [expected behavior]", () => {
    // Arrange
    // Act
    // Assert
  });
});
```

## 📖 Documentation Standards

### Code Comments
```clarity
;; Clear comment explaining purpose
(define-public (create-note (title (string-utf8 256)))
  ;; Implementation
)
```

### Commit Messages
- Use present tense ("add feature" not "added feature")
- Use imperative mood ("move cursor to..." not "moves cursor to...")
- Limit first line to 50 characters
- Reference issues and pull requests liberally

### Pull Request Descriptions
```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## Testing
Describe testing performed

## Checklist
- [ ] Tests pass
- [ ] Documentation updated
- [ ] No breaking changes
```

## ✅ Code Standards

### Clarity Code Style
```clarity
;; Use descriptive names
(define-constant FEE_AMOUNT u10000)

;; Comment complex logic
(define-public (create-note ...)
  ;; Validate inputs
  (asserts! (> (string-len title) u0) err-empty-title)
  
  ;; Update state
  (ok true)
)
```

### TypeScript/JavaScript
```typescript
// Use meaningful variable names
const noteCount = notes.length;

// Add JSDoc comments for functions
/**
 * Validates note content
 * @param content - Note text content
 * @returns true if valid
 */
function isValidContent(content: string): boolean {
  return content.length > 0;
}
```

## 🔒 Security Considerations

### Before Contributing
- Review `SECURITY.md` if available
- Understand Clarity security best practices
- Test for common vulnerabilities
- Never commit secrets or private keys

### Security Review
- All PRs undergo security review
- Critical issues must be reported privately
- Follow responsible disclosure guidelines

## 📊 Performance Guidelines

### Smart Contract Optimization
- Minimize storage operations
- Batch operations when possible
- Use appropriate data types
- Avoid deep recursion

### Testing Performance
- Keep test execution fast (<10 seconds)
- Use simnet for local testing
- Monitor gas costs in deployments

## 🎓 Learning Resources

### Clarity Documentation
- [Official Docs](https://docs.stacks.co/clarity)
- [Clarity by Example](https://claritybyexample.com)

### Stacks
- [Stacks Docs](https://docs.stacks.co/)
- [Developer Community](https://discord.gg/stacks)

### Smart Contract Security
- [Smart Contract Patterns](https://docs.stacks.co/smart-contracts)
- [Security Best Practices](https://docs.stacks.co/clarity)

## 💬 Communication

### Ask Questions
- Use GitHub Discussions for questions
- Join Stacks Discord for community help
- Check existing issues first

### Report Issues
- Use GitHub Issues for bug reports
- Include reproduction steps
- Provide context and environment info

### Code Review
- Be open to feedback
- Respond to review comments
- Request re-review when ready

## 🎉 Recognition

Contributors will be:
- Listed in project contributors
- Credited in release notes
- Recognized in documentation

## 📜 License

By contributing, you agree that your contributions will be licensed under the same license as the project.

---

Thank you for contributing to Notepad! 🙏

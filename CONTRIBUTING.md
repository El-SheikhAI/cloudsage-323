# Contributing to CloudSage

**Welcome!** 👋 We’re thrilled you’re considering contributing to CloudSage, our AI-driven cloud cost optimization tool. Your expertise helps make cloud management smarter and more affordable for everyone. This guide covers how to submit bug reports, propose features, and contribute code.

---

## First Things First 🚀

### Prerequisites
- **Git**: [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- **Node.js**: CloudSage requires Node.js **18.x** or newer. We recommend using [nvm](https://github.com/nvm-sh/nvm) for version management.
- **Cloud Accounts** (optional): A sandbox AWS/Azure/GCP account is useful for testing cost optimizations.

### Fork & Clone
1. **Fork** the [CloudSage repository](https://github.com/yourorg/cloudsage) (replace with actual URL).
2. **Clone** your fork locally:
   ```bash
   git clone https://github.com/your-username/cloudsage.git
   cd cloudsage
   ```
3. **Install dependencies**: Run `npm install`.

---

## How Can You Help?

### 🐛 Reporting Bugs
1. **Search existing issues** to avoid duplicates.
2. **Create a new issue** using the [Bug Report Template](link-to-template).
   - **Description**: Clearly explain the problem.
   - **Steps to Reproduce**: Include cloud provider, resource type, and code snippets (if applicable).
   - **Expected vs. Actual Behavior**
   - **Environment**: OS, Node.js version, CloudSage version.

### ✨ Requesting Features
1. **Search existing proposals** first.
2. **Open an issue** using the [Feature Request Template](link-to-template).
   - **Problem**: Describe the use case or pain point.
   - **Proposed Solution**: Share your vision (optional).
   - **Alternatives**: Any workarounds you’ve tried.

### 💻 Contributing Code
1. **Find an issue** labeled `good first issue` or `help wanted` (or discuss your idea in an issue first).
2. **Create a branch**: Use `feat/description` or `fix/description` (e.g., `feat/azure-resource-tagger`).
3. **Commit messages**: Follow [Conventional Commits](https://www.conventionalcommits.org/).
   - Example: `feat(azure): add storage cost analyzer`.
4. **Test your changes**: Run `npm test` and add new unit/integration tests if applicable.
5. **Check formatting**: Use `npm run lint` to verify style consistency.
6. **Open a Pull Request** (PR):
   - Reference the related issue (e.g., `Closes #123`).
   - Describe changes clearly and tag a maintainer for review.

---

## Code & Review Guidelines ✅

### Style
- **JavaScript/TypeScript**: Follow our [ESLint](https://eslint.org/) + [Prettier](https://prettier.io/) rules.
  ```javascript
  // Use async/await over callbacks where possible
  async function analyzeUsage(provider) {
    // ...
  }
  ```
- **Markdown**: Adopt clean headers, lists, and code fences (verified via [markdownlint](https://github.com/DavidAnson/markdownlint)).

### Tests
- **Coverage**: Maintain ≥90% test coverage. Run `npm run test:coverage`.
- **Mocks**: Use [Jest](https://jestjs.io/) for unit tests. Mock cloud APIs with [aws-sdk-mock](https://www.npmjs.com/package/aws-sdk-mock) or similar.

### Review Process
- **Be patient**: Maintainers will triage PRs within 3 business days.
- **Address feedback**: Update your PR promptly if changes are requested.
- **Merge**: All PRs require **two approvals** and passing CI checks.

---

## Community Conduct 🌈

We enforce a [Code of Conduct](CODE_OF_CONDUCT.md) to ensure a respectful, inclusive environment. Please treat all contributors with kindness and professionalism.

---

## License 📄

By contributing, you agree that your work will be licensed under CloudSage’s [MIT License](LICENSE).

**Thank you for making cloud cost optimization accessible to all!** 💙
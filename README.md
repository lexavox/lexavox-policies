# lexavox-policies

Official policy documents for LexaVox, including Privacy Policy, Terms of Service, Data Policy, Legal Notice, and Security Policy.

## Contents

- [PRIVACY.md](PRIVACY.md) - Privacy Policy
- [TERMS.md](TERMS.md) - Terms of Service
- [DATA_POLICY.md](DATA_POLICY.md) - Data Policy
- [LEGAL_NOTICE.md](LEGAL_NOTICE.md) - Legal Notice
- [SECURITY.md](SECURITY.md) - Security Policy

## Local Setup

To link this repository to your local development environment:

### Windows

```shell
# Create and navigate to your LexaVox directory
mkdir C:\LexaVox
cd C:\LexaVox

# Clone the repository
git clone https://github.com/lexavox/lexavox-policies.git

# The repository will be available at C:\LexaVox\lexavox-policies
```

### macOS / Linux

```shell
# Create and navigate to your LexaVox directory
mkdir -p ~/LexaVox
cd ~/LexaVox

# Clone the repository
git clone https://github.com/lexavox/lexavox-policies.git
```

## Keeping Policies in Sync

To pull the latest policy updates:

```shell
cd C:\LexaVox\lexavox-policies  # Windows
# or
cd ~/LexaVox/lexavox-policies   # macOS/Linux

git pull origin main
```

## Contributing

If you need to update policies:

1. Make your changes locally
2. Commit and push:
   ```shell
   git add .
   git commit -m "Update policy documents"
   git push origin main
   ```

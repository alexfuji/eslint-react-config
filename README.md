# @alexfuji/eslint-react-config

ESLint configuration for React projects with TypeScript support. Extends `@alexfuji/eslint-base-config`.

## Setup & Installation

> **Note**: This package is published to GitHub Packages. Authentication required.

### Configuration

Create `.env` file in project root:

```bash
GITHUB_TOKEN=your_github_token
```

Add to `.npmrc`:

```bash
@alexfuji:registry=https://npm.pkg.github.com/
//npm.pkg.github.com/:_authToken=${GITHUB_TOKEN}
```

> **Note**: In GitHub Actions, `NODE_AUTH_TOKEN` is automatically set from `GITHUB_TOKEN` secret.

### Generating a GitHub Token

1. Go to: https://github.com/settings/tokens
2. Click **Generate new token (classic)**
3. Give the token a descriptive name (e.g., "GitHub Packages Read")
4. Select the following **scope**:
   - `read:packages` - Read packages from GitHub Packages
5. Click **Generate token**
6. Copy the token and use it in the following commands

For CI/CD, add `GITHUB_TOKEN` as a secret environment variable in your CI platform.

### First Time Setup (Fresh Checkout)

Since the project needs dependencies from GitHub Packages, you need authentication to install:

**Option 1: Using env-cmd**

```bash
# Install env-cmd globally (required for the install script)
npm install -g env-cmd
```

Add the following script to the scripts in your `package.json`

```json
  "scripts": {
    "install:auth": "env-cmd -f .env npm install"
  },
```

```bash
# Run the install script
npm run install:auth
```

**Option 2: Direct environment variable**

```bash
# Set the token and install in one command
GITHUB_TOKEN=your_github_token npm install
```

## Usage

You'll need to install these peer dependencies:

```bash
npm install eslint@^9.0.0 react@^16.0.0 typescript-eslint
```

In your project's `eslint.config.js`:

```js
import reactConfig from '@alexfuji/eslint-react-config';
import tseslint from 'typescript-eslint';

export default tseslint.config(
  ...reactConfig,
  {
    rules: {
      // Custom rules for your project
    },
  },
);
```

## What's Included

- Extends `@alexfuji/eslint-base-config` (ESLint + TypeScript recommended rules)
- `eslint-plugin-react` - React-specific rules
- `eslint-plugin-react-hooks` - React Hooks rules (rules-of-hooks, exhaustive-deps)
- `eslint-plugin-jsx-a11y` - JSX accessibility rules

## Requirements

- ESLint 9+
- Node.js 18+
- React 16.3+ (for hooks rules)

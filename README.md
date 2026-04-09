# @alexfuji/eslint-react-config

ESLint configuration for React projects with TypeScript support. Extends `@alexfuji/eslint-base-config`.

## Configuration

**1. Create `.env` file in project root:**
```
GITHUB_TOKEN=your_github_token
```

**2. Add to `.npmrc`:**
```
@alexfuji:registry=https://npm.pkg.github.com/
//npm.pkg.github.com/:_authToken=${GITHUB_TOKEN}
```

> **Note**: In GitHub Actions, `NODE_AUTH_TOKEN` is automatically set from `GITHUB_TOKEN` secret.
GITHUB_TOKEN=your_github_token
```

**2. Add to `.npmrc`:**
```
@alexfuji:registry=https://npm.pkg.github.com/
//npm.pkg.github.com/:_authToken=${GITHUB_TOKEN}
```

### Generating a GitHub Token

1. Go to: https://github.com/settings/tokens
2. Click **Generate new token (classic)**
3. Give the token a descriptive name (e.g., "GitHub Packages Read")
4. Select the following **scope**:
   - `read:packages` - Read packages from GitHub Packages
5. Click **Generate token**
6. Copy the token and use it in the command above

For CI/CD, add `GITHUB_TOKEN` as a secret environment variable in your CI platform.

## Installation

> **Note**: This package is published to GitHub Packages. Authentication required (see below).

```bash
npm run install:auth
```

Or if using pnpm:

```bash
pnpm add @alexfuji/eslint-react-config
```

## Peer Dependencies

You'll need to install these packages or a higher version of this packages:

```bash
npm install eslint@^9.0.0 react@^16.0.0 typescript-eslint
```

## Usage

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

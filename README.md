# React + Storybook UI Component Library

This project is a comprehensive UI component library built with React, TypeScript, styled-components, and Storybook. It provides a collection of reusable, responsive, and accessible components that can be used across different projects.

## 📦 Getting Started

### Prerequisites

- Node.js 20 or higher
- Docker and Docker Compose

### Local Development

1. **Clone the repository**

   ```bash
   git clone https://github.com/senli-rrc/li_jason_coding_assignment13.git
   cd li_jason_coding_assignment13
   ```

2. **Install dependencies**

   ```bash
   cd li_jason_ui_garden_build_checks
   npm install --legacy-peer-deps
   ```

3. **Run Storybook locally**

   ```bash
   npm run storybook
   ```

   This will start Storybook on `http://localhost:8013`

4. **Run tests**
   ```bash
   npm run test
   ```

### Implement Pre-commit checks

This section outlines how to implement pre-commit checks using Husky, lint-staged, Prettier, and ESLint to ensure code quality before commits.

#### 📦 Step 1: Install the Necessary Dependencies

Use one of the following commands depending on your package manager:

**Using npm:**

```bash
npm install --save-dev husky lint-staged prettier eslint eslint-config-prettier eslint-plugin-prettier
```

**Using yarn:**

```bash
yarn add --dev husky lint-staged prettier eslint eslint-config-prettier eslint-plugin-prettier
```

#### 🛠 Step 2: Initialize Husky

Set up Husky to enable Git hooks in your project.

**For npm users:**

```bash
npx husky-init && npm install
```

**For yarn users:**

```bash
npx husky-init && yarn
```

This will:

- Create a `.husky` directory
- Add a sample pre-commit hook
- Update your `package.json` with a "prepare" script

#### ✅ Step 3: Create a Pre-commit Hook

Add a new pre-commit hook that runs lint-staged:

```bash
npx husky add .husky/pre-commit "npx lint-staged"
```

This creates a `.husky/pre-commit` file with the following content:

```bash
#!/usr/bin/env sh
. "$(dirname -- "$0")/_/husky.sh"

npx lint-staged --allow-empty
set CI=true && npm test
```

#### ⚙️ Step 4: Configure lint-staged

Add the following configuration to your `package.json`:

```json
{
  "lint-staged": {
    "*.{js,jsx,ts,tsx,json,css,scss,md}": ["prettier --write", "eslint --fix"]
  }
}
```

#### 🎨 Step 5: Configure Prettier

Create a `.prettierrc.json` file in your project root:

```json
{
  "semi": true,
  "singleQuote": true,
  "printWidth": 120,
  "trailingComma": "es5"
}
```

#### 🔍 Step 6: Configure ESLint

Create an `eslint.config.js` file for TypeScript support:

```javascript
import typescriptParser from "@typescript-eslint/parser";
import typescriptPlugin from "@typescript-eslint/eslint-plugin";

export default [
  {
    files: ["**/*.ts", "**/*.tsx"],
    languageOptions: {
      parser: typescriptParser,
      parserOptions: {
        ecmaVersion: "latest",
        sourceType: "module",
      },
    },
    plugins: {
      "@typescript-eslint": typescriptPlugin,
    },
    rules: {
      "@typescript-eslint/no-unused-vars": "warn",
      "@typescript-eslint/explicit-function-return-type": "off",
    },
  },
];
```

#### 🚀 Step 7: Test Your Setup

1. **Make a change** to any file
2. **Stage the changes**: `git add .`
3. **Commit**: `git commit -m "test pre-commit hooks"`

The pre-commit hooks should automatically:

- Format your code with Prettier
- Lint your code with ESLint
- Run tests (if configured)

#### Manual Commands

```bash
# Format code manually
npx prettier --write .

# Lint code manually
npx eslint . --fix

# Run tests manually
npm test

# Skip pre-commit hooks (not recommended)
git commit -m "your message" --no-verify
```

### 🐳 Docker Compose Development

For local development with Docker Compose (includes hot reload):

1. **Start the development environment**

   ```bash
   docker-compose -f docker-compose.yml up
   ```

   This will:
   - Build the development Docker image
   - Start Storybook with hot reload
   - Mount your local source code for live editing
   - Make Storybook available at `http://localhost:8013`

2. **Stop the development environment**

   ```bash
   docker-compose -f docker-compose.yml down
   ```

3. **Rebuild after dependency changes**
   ```bash
   docker-compose -f docker-compose.yml up --build
   ```
4. **Build a production**

   ```bash
   docker build -t li_jason_coding_assignment13 .
   ```

5. **Run the Image**
   ```bash
   docker run -p 8013:8013 li_jason_coding_assignment13
   ```

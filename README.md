# Configs

# VITE + REACT + TYPESCRIPT + ESLINT + PRETTIER+ VITEST  + TESTING LIBRARY😎

# VITE & REACT

```jsx
npm create vite@latest
```

Select React & Typescript

---

## ESLINT

```jsx
npm i -D eslint-config-standard-with-typescript eslint-plugin-import eslint-plugin-n eslint-plugin-promise eslint-plugin-react eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin
```

### .eslintrc.cjs:

```jsx
module.exports = {
  env: {
    browser: true,
    es2021: true,
  },
  extends: [
    'plugin:react/recommended',
    'plugin:react/jsx-runtime',
    'standard-with-typescript',
    'plugin:prettier/recommended',
  ],
  overrides: [],
  parserOptions: {
    project: 'tsconfig.json',
    ecmaVersion: 'latest',
    sourceType: 'module',
  },
  plugins: ['react', '@typescript-eslint', 'prettier'],
  rules: {
    'prettier/prettier': [
      'error',
      {
        endOfLine: 'auto',
      },
    ],
  },
}
```

### Add in tsconfig.json

```jsx
"include": [
	"vite.config.ts",
	".eslintrc.cjs",
	 "src"
]
```

---

# PRETTIER

```jsx
npm i -D prettier eslint-config-prettier eslint-plugin-prettier
```

## .prettierrc.cjs

```jsx
module.exports = {
  trailingComma: "es5",
  tabWidth: 2,
  semi: false,
  singleQuote: true,
}
```

---

# VITEST

```jsx
npm install -D vitest jsdom
```

### vite.config.ts

```jsx
/* eslint-disable @typescript-eslint/triple-slash-reference */
/// <reference types="vitest" />
/// <reference types="vite/client" />

import react from '@vitejs/plugin-react'
import { defineConfig } from 'vite'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [react()],
  test: {
    globals: true,
    environment: 'jsdom',
    setupFiles: ['./src/setupTests.ts'],
  },
})
```

## package.json

```jsx
"scripts": {
	...
	"test": "vitest"
}
```

### Create a ./src/setupTests.ts

---

# TESTING LIBRARY

```jsx
npm install --save-dev @testing-library/react @testing-library/jest-dom
```

### setUpTests.ts

```jsx
import matchers from '@testing-library/jest-dom/matchers'
import { expect } from 'vitest'

expect.extend(matchers)
```
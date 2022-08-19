---
layout: post
title: "prettier ‘ error"
categories:
  - Error
---

# prettier ‘ error

You can try something like this, it works for me.

package.json

```
  "devDependencies": {
    "eslint-plugin-prettier": "^3.1.1",
    "prettier": "^1.18.2"
  },

```

.eslintrc

```
{
  "extends": "react-app",
  "plugins": ["prettier"],
  "rules": {
    "prettier/prettier": "error"
  }
}

```

.prettierrc

```
{
  "semi": false,
  "trailingComma": "all",
  "singleQuote": true,
  "printWidth": 80,
  "tabWidth": 3
}
```

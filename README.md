# Vue 3 Bootstrap

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Type Support for `.vue` Imports in TS

TypeScript cannot handle type information for `.vue` imports by default, so we replace the `tsc` CLI with `vue-tsc` for type checking. In editors, we need [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin) to make the TypeScript language service aware of `.vue` types.

If the standalone TypeScript plugin doesn't feel fast enough to you, Volar has also implemented a [Take Over Mode](https://github.com/johnsoncodehk/volar/discussions/471#discussioncomment-1361669) that is more performant. You can enable it by the following steps:

1. Disable the built-in TypeScript Extension
   1. Run `Extensions: Show Built-in Extensions` from VSCode's command palette
   2. Find `TypeScript and JavaScript Language Features`, right click and select `Disable (Workspace)`
2. Reload the VSCode window by running `Developer: Reload Window` from the command palette.

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Type-Check, Compile and Minify for Production

```sh
npm run build
```

### Run Unit Tests with [Vitest](https://vitest.dev/)

```sh
npm run test:unit
```

### Run End-to-End Tests with [Cypress](https://www.cypress.io/)

```sh
npm run build
npm run test:e2e # or `npm run test:e2e:ci` for headless testing
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```

## Notes

### App Configurations

The application instance exposes a .config object that allows us to configure a few app-level options, for example defining an app-level error handler that captures errors from all descendant components:

```js
app.config.errorHandler = (err) => {
  /* handle error */
};
```

### Limitations of `reactive()`

1. It only works for object types (objects, arrays, and collection types such as `Map` and `Set`). It cannot hold primitive types such as `string`, `number` or `boolean`.
2. Since Vue's reactivity tracking works over property access, we must always keep the same reference to the reactive object. This means we can't easily "replace" a reactive object because the reactivity connection to the first reference is lost.

## 提問與整理

- [ ] `reactive` 與 `ref` API 的差別
- [ ] 何謂「組合函數」（Composables）？
- [ ] 何謂「可寫計算屬性」（Writable Computed）？
- [ ] `v-bind:class`、`v-if`、用法同 Vue 2

### 一些疑難雜症

VSCode version:

| Mac    | Win    |
| ------ | ------ |
| 1.72.1 | 1.60.X |

#### Template 相關

- [ ] ~~如何在 `<template>` 裡使用快捷鍵**註解**？~~
- [ ] ~~如何在 `<template>` 裡，使用 HTML 標籤提示與自填閉合標籤？~~
- [ ]

#### Script 相關

- [ ] ~~如何在 `<script>` 裡使用 intellisense？（例如：從 import 的地方推斷可解構的內容）~~
- [ ]

#### Eslint, Prettier & TypeScript 相關

- [ ] 在 `eslintrc.js` 加入自訂 eslint 規則之後，造成 eslint 與 prettier 的 format 衝突
- [ ]

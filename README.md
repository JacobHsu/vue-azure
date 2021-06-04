# Vue 3 + Typescript + Vite

This template should help get you started developing with Vue 3 and Typescript in Vite.

[Vite](https://v3.cn.vuejs.org/guide/installation.html#vite)  
`$ npm init @vitejs/app <project-name>`  

## Azure

[在 Azure 中建立 Node.js Web 應用程式](https://docs.microsoft.com/zh-tw/azure/app-service/quickstart-nodejs?pivots=platform-linux)  
[在 Azure App Service 中建立發行設定檔案](https://docs.microsoft.com/zh-tw/visualstudio/deployment/tutorial-import-publish-settings-azure?view=vs-2019)  
[使用 GitHub Actions 部署到 App Service](https://docs.microsoft.com/zh-tw/azure/app-service/deploy-github-actions?tabs=applevel)

## github

### Settings

github > Settings > secrets

Nmae `AZURE_WEBAPP_PUBLISH_PROFILE`  
Value `App Service > 取得發行設定檔 > vue-azure.PublishSettings`

### Actions

Deploy your code with these popular services > Deploy Node.js to Azure Web App

vue-azure / .github / workflows / azure.yml

```js
on: push

env:
  AZURE_WEBAPP_NAME: vue-azure    # set this to your application's name
  AZURE_WEBAPP_PACKAGE_PATH: 'dist'      # set this to the path to your web app project, defaults to the repository root
  NODE_VERSION: '10.x'                # set this to the node version to use
```

Actions > All workflows > 1 workflow run

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Vetur](https://marketplace.visualstudio.com/items?itemName=octref.vetur). Make sure to enable `vetur.experimental.templateInterpolationService` in settings!

### If Using `<script setup>`

[`<script setup>`](https://github.com/vuejs/rfcs/pull/227) is a feature that is currently in RFC stage. To get proper IDE support for the syntax, use [Volar](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.volar) instead of Vetur (and disable Vetur).

## Type Support For `.vue` Imports in TS

Since TypeScript cannot handle type information for `.vue` imports, they are shimmed to be a generic Vue component type by default. In most cases this is fine if you don't really care about component prop types outside of templates. However, if you wish to get actual prop types in `.vue` imports (for example to get props validation when using manual `h(...)` calls), you can use the following:

### If Using Volar

Run `Volar: Switch TS Plugin on/off` from VSCode command palette.

### If Using Vetur

1. Install and add `@vuedx/typescript-plugin-vue` to the [plugins section](https://www.typescriptlang.org/tsconfig#plugins) in `tsconfig.json`
2. Delete `src/shims-vue.d.ts` as it is no longer needed to provide module info to Typescript
3. Open `src/main.ts` in VSCode
4. Open the VSCode command palette
5. Search and run "Select TypeScript version" -> "Use workspace version"

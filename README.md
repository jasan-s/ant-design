## codefree_ant

### Reason for Fork: To avoid style classes conflict with codefree host apps also using antd lib

### NOTES on keeping Fork UpToDate:

- make sure upstream is set using `git remote add upstream git@github.com:ant-design/ant-design.git`
- make sure your on local `master` branch of this fork
- `git fetch upstream`
- `git rebase upstream/master` (this will move my forked changes(renamed `@ant-prefix` & package name in `package.json` to `codefree_ant`) to top of history tree)

### NOTES on publishing new version of `codefree_ant` to npm after fork update:

- make sure `node` version is `>=` `11.4` use `nvm`
- run `npm i`
- update the version in `package.json`
- run `rimraf package-lock.json`
- run `npm run pub -f`

### NOTES on usage of this forked lib in SPA

- make sure `npm` version is `>=` `6.9.0`
- run `npm i --save antd@npm:codefree_ant`
- import `import { ConfigProvider } from 'antd'` in the root container of SPA
- Wrap root return with ConfigProvider (which will add custom prefix(`codefree_ant`, matches `@ant-prefix`) to all antd components classes)
  ```
  <ConfigProvider prefixCls="codefree_ant">
  <RootContainer {...this.props} />
  </ConfigProvider>
  ```
- if importing `antd` css styles then add `@import '~antd/dist/codefree_ant.css';` in main root `css` file.

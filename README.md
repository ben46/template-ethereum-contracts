# Boilerplate for ethereum solidity smart contract development

## INSTALL

```bash
yarn
```

## SCRIPTS
 
### `yarn prepare`

As a standard lifecycle npm script, it is executed automatically upon install. It generate config file and typechain to get you started with type safe contract interactions
<br/><br/>

### 本地运行节点, 热更新, 适用于开发(前端连接到合约开发的个人电脑 rpc,联调)

`yarn dev`

`yarn local:dev`

### 测试部署, 只存在内存中

`yarn void:deploy                                                       `

### 运行单元测试

`yarn test`

### fork 部署

`yarn fork:deploy base_sepolia`

### 部署

`yarn deploy base_sepolia`

输出文件在 deployments 中, 一个文件里面包含合约地址, abi, 等全部信息

### 验证合约

`yarn verify base_sepolia`

### 上传到 tenderly

`yarn tenderly:push base_sepolia`

### 导出单个文件给前端

`yarn export base_sepolia export/base_sepolia.json`

### 升级合约

todo

### fork 运行脚本

`yarn fork:run base_sepolia <file.ts> [args...]`

### 运行脚本

`yarn run base_sepolia <file.ts> [args...]`

### fork 链上合约, 运行测试脚本

`yarn fork:test <network> [--blockNumber <blockNumber>] [mocha args...]`

This will test the contract against a temporary fork of the specified network.


### forge

```bash
forge test
```

This require the installation of forge (see [foundry](https://github.com/gakonst/foundry))

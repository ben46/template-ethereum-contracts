以太坊Solidity智能合约开发的样板

## 安装

```bash
yarn
```

## 测试

有3种测试方式: hardhat，dapptools和forge

### hardhat

- 使用hardhat进行测试，可以利用hardhat-deploy来重用部署过程和命名帐户：

```bash
yarn test
```

### [dapptools](https://dapp.tools)

```bash
dapp test
```

后者需要额外的步骤来设置您的机器：

安装dapptools（请参考[这里](https://github.com/dapphub/dapptools#installation)的说明）：

```bash
# 用户必须在sudoers中
curl -L https://nixos.org/nix/install | sh

# 运行此命令或重新登录以使用Nix
. "$HOME/.nix-profile/etc/profile.d/nix.sh"

curl https://dapp.tools/install | sh
```

然后安装具有正确版本的solc：

```bash
nix-env -f https://github.com/dapphub/dapptools/archive/master.tar.gz -iA solc-static-versions.solc_0_8_9
```

### forge

```bash
forge test
```

这需要安装forge（请参考[foundry](https://github.com/gakonst/foundry)）

## 脚本

这里是您可以执行的npm脚本列表：

其中一些依赖于[./\_scripts.js](./_scripts.js)，以允许通过命令行参数对其进行参数化（如果需要修改，请查看其中的内容）
<br/><br/>

### `yarn prepare`

作为标准的生命周期npm脚本，在安装时会自动执行。它会生成配置文件和typechain，以让您可以开始进行类型安全的合约交互
<br/><br/>

### `yarn format` 和 `yarn format:fix`

这些命令将检查代码的格式。`:fix`版本将修改文件以符合`.prettierrc.`中指定的要求
<br/><br/>

### `yarn compile`

这些命令将编译您的合约
<br/><br/>

### `yarn void:deploy`

这将在内存中的hardhat网络上部署您的合约，然后退出，不留痕迹。这是一种快速确保部署按预期工作且没有后果的方式
<br/><br/>

### `yarn test [mocha参数...]`

这将使用mocha执行您的测试。您可以向mocha传递额外的参数
<br/><br/>

### `yarn coverage`

这将在`coverage/`文件夹中生成覆盖率报告
<br/><br/>

### `yarn gas`

这将为测试中使用的函数生成gas报告
<br/><br/>

### `yarn dev`

这将在 `localhost:8545` 上运行一个本地的hardhat网络，并在其上部署您的合约。此外，它将监视任何更改并重新部署它们
<br/><br/>

### `yarn local:dev`

这假设在 `localhost:8545` 上运行一个本地节点。它将在该节点上部署您的合约。此外，它将监视任何更改并重新部署它们
<br/><br/>

### `yarn execute <网络> <文件.ts> [参数...]`

这将针对指定的网络执行脚本 `<文件.ts>`
<br/><br/>

### `yarn deploy <网络> [参数...]`

这将在指定的网络上部署合约。

在幕后它使用`hardhat deploy`命令，因此您可以附加任何参数
<br/><br/>

### `yarn export <网络> <文件.json>`

这将将部署的合约的abi+地址导出到 `<文件.json>`
<br/><br/>

### `yarn fork:execute <网络> [--blockNumber <块号>] [--deploy] <文件.ts> [参数...]`

这将针对指定网络的临时分叉执行脚本 `<文件.ts>`

如果使用 `--deploy`，将执行部署脚本
<br/><br/>

### `yarn fork:deploy <网络> [--blockNumber <块号>] [参数...]`

这将针对指定网络的临时分叉部署合约。

在幕后它使用`hardhat deploy`命令，因此您可以附加任何参数
<br/><br/>

### `yarn fork:test <网络> [--blockNumber <块号>] [mocha参数...]`

这将针对指定网络的临时分叉测试合约
<br/><br/>

### `yarn fork:dev <网络> [--blockNumber <块号>] [参数...]`

这将针对指定网络的分叉部署合约，并将其保持作为节点运行。

在幕后它使用`hardhat node`命令，因此您可以附加任何参数
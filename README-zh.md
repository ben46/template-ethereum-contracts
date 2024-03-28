## `yarn deploy <网络> [参数...]`

这将在指定的网络上部署合约。

在幕后它使用`hardhat deploy`命令，因此您可以附加任何参数
<br/><br/>

`hardhat --network <网络> deploy --report-gas [参数...]`
<br/><br/>

#### **选项**

`--export <filepath>`: 导出一个包含当前网络上所有合约（地址、abi 和额外数据）的文件。该文件包含最少的信息，以避免使前端臃肿。

`--export-all <filepath>`: 导出包含所有保存的部署中的所有合约的文件，无论当前调用的网络是哪个。

`--tags <tags>`: 只执行带有给定标签（用逗号分隔）及其依赖项的部署脚本（有关标签和依赖项的更多信息，请参见[这里](#deploy-scripts-tags-and-dependencies)）

`--gasprice <gasprice>`: 指定默认用于通过**hardhat-deploy**助手在部署脚本中执行的交易的 gas 价格（以 wei 为单位）

`--write <boolean>`: 默认为 true（对于 hardhat 网络除外）。如果为 true，则将部署保存到磁盘上（在部署路径中，参见[路径配置](#extra-paths-config)）。

#### **标志**

`--reset`: 此标志从头开始重置部署。之前部署的合约不会被考虑，并从磁盘中删除。

`--silent`: 此标志移除**hardhat-deploy**的日志输出（请查看[`hre.deployments`](#the-deployments-field)的日志函数和日志选项）

`--watch`: 此标志使任务不断进行，监视部署脚本文件夹和合约源代码文件夹中的文件更改。如果发生任何更改，合约将被重新编译，部署脚本将被重新运行。与代理部署（[Proxies](#deploying-and-upgrading-proxies)或[Diamond](#builtin-in-support-for-diamonds-eip2535)）结合使用，可以实现 HCR（Hot Contract Replacement，热合约替换）功能。

## `yarn local:dev`

等于运行了这行命令
`hardhat --network localhost deploy --watch`
<br/><br/>

这假设在 `localhost:8545` 上运行一个本地节点。它将在该节点上部署您的合约。此外，它将监视任何更改并重新部署它们
<br/><br/>

## `yarn dev`

这将在 `localhost:8545` 上运行一个本地的 hardhat 网络，并在其上部署您的合约。--watch 开启了热部署, 任何合约上的改动都会实时生效. 此外，它将监视任何更改并重新部署它们
<br/><br/>

等于运行了这行命令
`cross-env MINING_INTERVAL=\"3000,5000\" hardhat node --hostname 0.0.0.0 --watch`

## `yarn execute <网络> <文件.ts> [参数...]`

这将针对指定的网络执行脚本 `<文件.ts>`
<br/><br/>

`cross-env HARDHAT_DEPLOY_LOG=true HARDHAT_NETWORK=<网络> ts-node --files <文件.ts> [参数...]
`

## `yarn export <网络> <文件.json>`

这将将部署的合约的 abi+地址导出到 `<文件.json>`
<br/><br/>

## `yarn fork:execute <网络> [--blockNumber <块号>] [--deploy] <文件.ts> [参数...]`

这将针对指定网络的临时分叉执行脚本 `<文件.ts>`

如果使用 `--deploy`，将执行部署脚本
<br/><br/>

## `yarn fork:deploy <网络> [--blockNumber <块号>] [参数...]`

这将针对指定网络的临时分叉部署合约。

在幕后它使用`hardhat deploy`命令，因此您可以附加任何参数
<br/><br/>

## `yarn fork:test <网络> [--blockNumber <块号>] [mocha参数...]`

这将针对指定网络的临时分叉测试合约
<br/><br/>

## `yarn fork:dev <网络> [--blockNumber <块号>] [参数...]`

这将针对指定网络的分叉部署合约，并将其保持作为节点运行。

在幕后它使用`hardhat node`命令，因此您可以附加任何参数

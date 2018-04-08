## Yarn Cmd

* 所有的操作，在会随时在 package.json 和 yarn.lock 中响应更新

```bash
# 初使化
yarn init

# 安装包
yarn add [package]                      # 安装到 dependencies 中
yarn add [package]@[version]
yarn add [package]@[tag]

yarn add --dev [package]                # 安装到 devDependeccies 中
yarn add --peer [package]               # 安装到 peerDependeccies 中
yarn add --optional [package]           # 安装到 optionalDependeccies 中

# 安装所有包
yarn
yarn install

# 更新包
yarn upgrade [package]

# 删除包
yarn remove [package]



``` 


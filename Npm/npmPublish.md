## 发布自己的 npm 包

#### 注意事项
* 发布的包的目录下须有 package.json 文件，并记录相关信息
* 主入口需要有一个 index.js，参考其他包构建
* 使用`.gitignore` 或 `.npmignore`来屏蔽不想发布的文件
* 如果使用了淘宝镜像，注意需要切回来
```bash
npm config set registry http://registry.npmjs.org
```

#### 准备工作
* 阅读一下 npm 条例与政策 [npmjs.policies](https://www.npmjs.com/policies)
* 创建一个 npm 账号
* 检查你的账号是否存在：
```bash
https://www.npmjs.com/~<username>
```

#### 开始
```bash
> npm login             # 会提示输入 username/password/email等，登录完之后会有提示
> npm logout            # 登出
> npm whoami            # 查看当前身份
# 
> npm publish <package-name>                # 发布包
> npm unpublish <package-name> --force      # 退回包
> # 可以 cd 到包目录进行发布
```


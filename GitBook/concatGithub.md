## GitBook concat Github repository

#### GitBook 创建电子书并与Github仓库结合
* Github --> create new repository
* Gitbook --> create a new book(choose `BOOK & MANUAL`, and set Title and Description)
* Gitbook --> choose the new book you created above 
* Gitbook --> choose `SETTINGS` 
* Gitbook --> choose `Github` --> select a Repository

#### 以下步骤可能必要（或非必要，因为版本不同了）
* Gitbook --> choose `Hooks` --> Add `webhook`, set your github repository .git and secret
* Gitbook --> choose `Github` --> copy Webhook url
* Github --> select your repository --> select `Settings` --> select `webhooks` --> add the Webhook url


#### gitbook 编辑
* 在 gitbook 上选择刚刚 create 的 book
* 点击编辑，添加一个目录，一个文章，以便生成 Summary


#### 查看 github 上的仓库
* 查看 github 上与之关联的仓库，如果 Summary.md 生成了，则表示成功
* 可 download github 上的库，并开始编辑，随时更新 github

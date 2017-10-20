##### git初始化
`git init`
##### add
- 添加全部更改`git add .`
- 添加指定更改`git add xx`


##### commit
- 添加当前更改信息`git commit -m "xx"`
- 添加所有更改信息`git commit -am "xx"`

##### 添加远程仓库
`git remote add origin https://github.com/xielingwei/xx.git`
##### pull
`git pull origin xx`
##### push
`git push origin xx`
##### git当前版本
`git rev-parse HEAD`

##### git回退到指定版本
`git reset --hard xxx`

##### git提交记录
`git log`
##### git修改原文件为markdown格式
`git mv xx xx.md`
##### git分支管理
- 新建从分支并切换至新分支`git checkout -b xx`
- 切换分支`git checkout xx`
- 合并某分支到h当前所在分支`git merge xx`

##### git复制远程分支
- `git clone -b hotline_newest http://git.hisuite-hand.com/hisuite-team/hisuite.git`
- `git clone -b ccc_new http://rdc.hand-china.com/gitlab/rdc_hi/ironmine.git`
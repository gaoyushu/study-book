# gitbook

1.2020.10.1后版本更新 master变为main
2.注意gitbook和nodejs版本问题 nodejs版本过高travisci中gitbook build会报错 // 暂没解决

## 1.基操  gitbook
1. 创建一个仓库 在本地`git clone`
2. `npm i gitbook-cli -g // 全局安装gitbook命令行  `
   `gitbook -V // 查看版本状态  `
3. `gitbook init // 生成两个文件：README.md一般为首页 SUMMARY.md 左侧目录超链接合集  `
4. `gitbook build // 构建成功 生成_build文件夹 ` 
5. `gitbook serve // 本地浏览  `
   http://localhost:4000 // 浏览器本地查看gitbook 如果未build会自动先gitbook build  
6. `git checkout -b gh-pages // 创建浏览分支 将构建的文件放在gh-pages 提交展示  `
7. push构建的内容到gh-pages上  
   `cd ./_book  `
   `git init  `
   `git add .  `
   `git commit -m 'publish'  `
   `git push -f -quiet 'https://github.com/gaoyushu/study-book' master:gh-pages // 此时远程仓库gh-pages下有push的代码  `
8. push master分支内容
   `cd ..`
   `rm -rf _book`
   `git add .`
   `git commit -m 'new page'`
   `git push // 此时master分支下代码上传  `
9. https://gaoyushu.github.io/spa-gitbook/ // 浏览线上gitbook

## 2.自动化构建  travisci
* 前提准备
创建ACC_TOKEN
![](/imgs/gitbook/accesstoken0.png) 
![](/imgs/gitbook/accesstoken1.png) 
![](/imgs/gitbook/accesstoken2.png) 

1. `npm init` // 生成package.json  
2. 将package.json文件中 exit 1 修改为 exit 0
![](/imgs/gitbook/packagejson.png) 
3. 创建.travis.yml文件 将需要自动化的操作写入
![](/imgs/gitbook/travisyml.png) 
4. `git push origin master`
5. https://travis-ci.org/ 在travisci上选择相应仓库 配置五项Environment Variables
   更多了解 http://www.ruanyifeng.com/blog/2017/12/travis_ci_tutorial.html
   ![](/imgs/gitbook/travisci1.jpg) 
   ![](/imgs/gitbook/travisci2.png) 
6. 新push一个页面 commit有√ travisci build绿色成功
   ![](/imgs/gitbook/success1.png) 
   ![](/imgs/gitbook/success2.png) 
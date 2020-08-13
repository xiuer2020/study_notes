###########环境依赖
node v6.13.4

###########部署步骤
1. 路径'server'                      执行'npm install' 命令, 安装node运行环境
2. 路径'server/config/confing.js'    更改数据库信息, 包括:数据库名称, 数据库用户名, 数据库密码, 数据地址
3. 路径'server'                      执行'nodemon index.js' 命令, 运行服务器
###########目录结构描述
├── Readme.md                    // help
├── app                          // 应用
|── .browserslistrc              // 文件用于设置浏览器的兼容
|── public/index.html            // BASE_URL 静态路径变量
|── .eslintrc                    // 文件用于代码规则配置
|── .gitignore                   // 文件用于过滤 git 文件提交 
|── package.json                 // 文件其实就是对项目或者模块包的描述，里面包含许多元信息。比如项目名称，项目版本，项目执行入口文件，
|── package-lock.json            // 文件用于锁定安装时的包的版本号
|── babel.config.js              // babel 配置
|── vue.config.js                // vue 配置
├── publick                      // 静态目录
│   |── index.html
├── src
|   |── componets                // 组件文件夹
|   |── views                    // 视图组件文件夹
|   |── store                    // vuex store文件夹
|   |── router                   // 路由文件夹
|   |── api                      // api 文件夹
|   |── assets                   // 资源文件夹
|   |── plugins                  // 插件文件夹
|   |── main.js                  // 入口文件




########### 其他
项目仅仅做了前后端分离和添加数据到'Call'表



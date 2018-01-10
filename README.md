ATF 2.0 版本不再使用1.0版本的fis3构建方式，采用 vue-cli 构建多页面应用。

## 开发
```bash
    # 克隆项目
    git clone https://github.com/cqs-fe/ATF-2.0.git

    # 安装依赖
    npm install

    # 本地开发 开启服务
    npm run dev
```
浏览器访问 http://localhost:8088

## 发布
```bash
    npm run build
```
## 项目目录

```
├── README.md
├── build   //构建相关
│   ├── build.js
│   ├── check-versions.js
│   ├── dev-client.js
│   ├── dev-server.js
│   ├── utils.js
│   ├── vue-loader.conf.js
│   ├── webpack.base.conf.js
│   ├── webpack.dev.conf.js
│   └── webpack.prod.conf.js
├── config   //配置相关
│   ├── dev.env.js
│   ├── index.js
│   └── prod.env.js
├── package.json
├── src      //源代码
│   ├── assets //资源文件
│   │   └── css
│   │   └── js
│   │   └── images
│   ├── components //公共组件
│   │   ├── sidebar.vue
│   │   └── header-guide.vue
│   └── pages  //页面文件
│       ├── aut
│       │   ├── aut.html
│       │   ├── aut.js
│       │   └── aut.vue
│       └── testProject
│           ├── testProject.html
│           ├── testProject.js
│           ├── testProject.vue
│           └── router
│               └── index.js
└── static    //外部库静态资源（为便于版本迁移，暂时均放在了assets中）
```




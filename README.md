# docsify-sidebar-gen

用来对本地文件存储的MD文件进行网页浏览，使用了docsify，并对页面进行了微调；配合gen-sidebar.py脚本生成_sidebar.md侧边栏数据，就可以方便预览md笔记了。

## 使用

有如下Note目录：
```
.
├── 目录1
│   ├── MD1.md
│   └── 目录1
│       └── MD1.md
└── 目录2
    └── MD1.md
```

现在将本项目复制进去，目录结构变成下面这样：
```
.
├── assets
│   ├── docsify.min.js
│   ├── docsify-sidebar-collapse.js
│   ├── jquery.slim.min.js
│   ├── search.min.js
│   └── theme-simple-dark.css
├── gen-sidebar.py
├── index.html
├── 目录1
│   ├── MD1.md
│   └── 目录1
│       └── MD1.md
└── 目录2
    └── MD1.md
```

用python3运行gen-sidebar.py脚本，会生成一个_sidebar.md文件，并且使用python3开启了一个8000端口的http服务器：
```
.
├── ...
├── _sidebar.md
├── ...
```
_sidebar.md文件内容如下：
```
- [目录1](#)
    - [MD1](%E7%9B%AE%E5%BD%951/MD1)
    - [目录1](#)
        - [MD1](%E7%9B%AE%E5%BD%951/%E7%9B%AE%E5%BD%951/MD1)
- [目录2](#)
    - [MD1](%E7%9B%AE%E5%BD%952/MD1)
```

访问 http://127.0.0.1:8000/ 就能看到带侧边栏的Docsify页面，并且侧边栏支持折叠和记忆（docsify-sidebar-collapse.js相对与原版加入了记录能力）。
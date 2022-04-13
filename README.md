# SDDantes.github.io
SDDantes/Mirrdark's Personal Blog

Supported by Hexa and Obsidian



电脑间迁移须知：

感谢@Candinya提供的[Kratos-Rebirth主题](https://github.com/Candinya/Kratos-Rebirth)

使用git clone此仓库，并切换到source分支。

下载[nvs](https://github.com/jasongin/nvs)的msi安装包。

cmd运行nvs，安装合适的node版本，由于使用了Kratos-Rebirth主题，根据其文档，建议安装Node V14或更高版本。（更高版本有潜在的与hexo不兼容的问题）

选择node环境，安装hexo。

```
npm install -g hexo-cli
```

然后进入路径`SDDantes.github.io/blog`内，运行：

```
npm install
npm audit fix
npm install hexo-deployer-git --save
npm audit fix
npm install
npm audit fix
```

之后请阅读主题的使用说明。



这里没有Q&A，因为不应该出现任何问题（程序员经常说这种话）。
<h1> Gitea - Git with a cup of tea</h1>
当前 Docker 内置 Gitea v1.12.5 版本

## 配置
使用此docker-compose文件可以快速启动并运行。您应该更改mysql用户名和root密码。安装时，您可以将数据库容器引用为主机db。
此配置将公开公开端口3000和22。

挂载目录 /test 到  /data , 数据将存储到 /test
     
```
version: '2'
services:
  web:
    image: gitea/gitea:1.12.4
    volumes:
      - ./data:/data
    ports:
      - "3000:3000"
      - "22:22"
    depends_on:
      - db
    restart: always
  db:
    image: mariadb:10
    restart: always
    environment:
      - MYSQL_ROOT_PASSWORD=changeme
      - MYSQL_DATABASE=gitea
      - MYSQL_USER=gitea
      - MYSQL_PASSWORD=changeme
    volumes:
      - ./db/:/var/lib/mysql

```

      

## 目标

Gitea 的首要目标是创建一个极易安装，运行非常快速，安装和使用体验良好的自建 Git 服务。我们采用 Go 作为后端语言，这使我们只要生成一个可执行程序即可。并且他还支持跨平台，支持 Linux, macOS 和 Windows 以及各种架构，除了 x86，amd64，还包括 ARM 和 PowerPC。

如果您想试用一下，请访问 [在线Demo](https://try.gitea.io/)！

## 提示

1. **开始贡献代码之前请确保你已经看过了 [贡献者向导（英文）](CONTRIBUTING.md)**.
2. 所有的安全问题，请私下发送邮件给 **security@gitea.io**。谢谢！
3. 如果你要使用API，请参见 [API 文档](https://godoc.org/code.gitea.io/sdk/gitea).

## 文档

关于如何安装请访问我们的 [文档站](https://docs.gitea.io/zh-cn/)，如果没有找到对应的文档，你也可以通过 [Discord - 英文](https://discord.gg/gitea) 和 QQ群 328432459 来和我们交流。

## 贡献流程

Fork -> Patch -> Push -> Pull Request

## 作者

* [Maintainers](https://github.com/orgs/go-gitea/people)
* [Contributors](https://github.com/go-gitea/gitea/graphs/contributors)
* [Translators](options/locale/TRANSLATORS)

## 授权许可

本项目采用 MIT 开源授权许可证，完整的授权说明已放置在 [LICENSE](https://github.com/go-gitea/gitea/blob/master/LICENSE) 文件中。

## 截图

|![Dashboard](https://dl.gitea.io/screenshots/home_timeline.png)|![User Profile](https://dl.gitea.io/screenshots/user_profile.png)|![Global Issues](https://dl.gitea.io/screenshots/global_issues.png)|
|:---:|:---:|:---:|
|![Branches](https://dl.gitea.io/screenshots/branches.png)|![Web Editor](https://dl.gitea.io/screenshots/web_editor.png)|![Activity](https://dl.gitea.io/screenshots/activity.png)|
|![New Migration](https://dl.gitea.io/screenshots/migration.png)|![Migrating](https://dl.gitea.io/screenshots/migration.gif)|![Pull Request View](https://image.ibb.co/e02dSb/6.png)
![Pull Request Dark](https://dl.gitea.io/screenshots/pull_requests_dark.png)|![Diff Review Dark](https://dl.gitea.io/screenshots/review_dark.png)|![Diff Dark](https://dl.gitea.io/screenshots/diff_dark.png)|

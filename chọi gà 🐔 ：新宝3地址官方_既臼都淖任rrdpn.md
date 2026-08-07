新宝3地址官方【Q-——333307——】新宝3地址官方【 辋芷《888yx●vip》 】
新宝3地址官方【Q-——333307——】新宝3地址官方【 辋芷《888yx●vip》 】

 从零到一：用 GitHub Actions 实现自动化部署，告别手动运维

你是不是也遇到过这样的场景：代码写好了，`git push` 之后还要手动登录服务器拉代码、重启服务？繁琐不说，还容易出错。今天咱们聊聊如何用 GitHub Actions 把这套流程彻底自动化，让你的项目真正做到“推完即上线”。

 什么是 GitHub Actions？

简单说，它是 GitHub 官方提供的 CI/CD 服务。你只需要在仓库里放一个 YAML 格式的工作流文件，GitHub 就会在特定事件发生时（比如 `push` 代码、提 `PR`）自动执行你定义的任务。

 关键词：自动化部署、CI/CD、嵌入式

对，你没看错，嵌入式开发也能用。之前很多同学觉得这东西是 Web 后端专属，其实给单片机上编译固件、跑测试，用 Actions 同样香。GitHub Actions 在嵌入式 CI 场景下的应用，这几年增长特别快。

 三步上手，快速配置

第一步，建工作流文件。在项目根目录创建 `.github/workflows/deploy.yml`：

```yaml
name: 自动部署
on:
  push:
    branches: [ main ]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: npm install
      - run: npm run build
      - uses: appleboy/scp-action@v0.1.7
        with:
          host: ${{ secrets.SERVER_HOST }}
          username: ${{ secrets.SSH_USER }}
          key: ${{ secrets.SSH_PRIVATE_KEY }}
          source: "dist/"
          target: "/var/www/html"
```

第二步，配置 Secrets。去仓库的 Settings -> Secrets and variables -> Actions，添加 `SERVER_HOST`、`SSH_USER`、`SSH_PRIVATE_KEY` 这三个变量，密码和密钥别写死在代码里。

第三步，推送验证。把工作流推送到仓库后，点击 Actions 页面，就能看到构建进度条了。绿了，就说明部署成功。

 排查快 N 倍的小技巧

如果部署失败，点开失败的那次运行记录，上下文日志都是实时输出的，比看服务器日志找原因快得多。另外建议在 YAML 里加个 `timeout-minutes`，比如 10 分钟，防止某个步骤卡死浪费你时间。

 部署完，然后呢？

你可以把 `GitHub Actions` 和 `fork` 玩法结合，别人提 `PR` 时自动跑格式检查；也可以设置定时任务，定期拉取上游代码合并，自动生成 `Changelog`。自动化的上限取决于你的想象力。

如果你今天正好想试试水，选一个小项目（或者静态博客）直接套上面的模板，推一次就知道这套流程多省心。评论区聊聊你准备自动化哪个环节？遇到问题我也会帮你看看。

相关推荐：

https://github.com/brownthomas7094/agggnp/blob/main/Th%E1%BB%83%20thao%20%E2%9A%BD%EF%B8%8F%EF%BC%9A%E6%96%B0%E5%AE%9D3%E5%9C%B0%E5%9D%80%E5%BC%80%E6%88%B7_%E5%B1%AF%E6%BB%A9%E8%AE%AF%E5%BC%8F%E8%87%80dwdcx.md

<img src="https://i.postimg.cc/3NvfSyM8/mei-nu-bei-jing-zhao-shang-tu-zhi-zuo-(22).png" />

相关推荐：

https://github.com/brownthomas7094/agggnp/commit/f1ecdcf6534cbde31719256fc3296e1a5db95f0f

<img src="https://i.postimg.cc/FzLCWftP/mei-nu-bei-jing-zhao-shang-tu-zhi-zuo-(25).png" />
相关推荐：

https://github.com/stewartpamela7264/qbqsmb/blob/main/ch%E1%BB%8Di%20g%C3%A0%20%F0%9F%90%94%20%EF%BC%9A%E6%96%B0%E5%AE%9D3%E5%9C%B0%E5%9D%80%E6%B5%8B%E9%80%9F_%E8%A0%A2%E5%87%B9%E5%8B%A4%E5%BD%BB%E7%AA%83yfaix.md

<img src="https://i.postimg.cc/fLFgfcPy/mei-nu-bei-jing-zhao-shang-tu-zhi-zuo-(21).png" />
相关推荐：

https://github.com/stewartpamela7264/qbqsmb/commit/264273060efc67610781f9cc3e46086657723801

<img src="https://i.postimg.cc/3NvfSyM8/mei-nu-bei-jing-zhao-shang-tu-zhi-zuo-(22).png" />

资讯来源：新华网、人民网、央视新闻、中新网、凤凰网、澎湃新闻、界面新闻、新浪新闻、搜狐网、财新网、观察者网、第一财经等主流平台，以独树一帜的观察视角与扎实的深度报道能力，在资讯领域收获广泛关注。

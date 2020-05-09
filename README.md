# EpicGames Giveaways Auto Claimer

充分~~白嫖~~使用 **每月免费2000分钟**的 **Github Actions** (逃

1.  `Get_Epic_Game.yml` : 用于定时获取 Epic Game 发放的周免游戏。

# 配置方法

在 GitHub 的 'Settings' - 'Secrets' 添加 EMAIL (你的 Epic 邮箱)，PASSWD (你的 Epic 密码)，SECRET（二步验证 Secret）。

二步验证的 Secret 在 EpicGames 启用二步验证、扫描二维码的时候会显示。如果你已经启用了，那么关闭再启用即可看到。

并且，修改 .github/workflows/Get_Epic_Game.yml 文件，去掉开头的 `#` 号，如下：

```yaml
on:
  schedule: # 删除本行开头的 # 号
    - cron: "25 2 * * *" # 删除本行开头的 # 号
  push:
    branches:
      - master
```

# 备注

- 由于脚本不知道为何有概率失败，而且 Epic 有时候会中途添加游戏，因此触发时间我改成了每天一次。

- 由于几次尝试发现如果只有 Schedule 的配置，似乎 GitHub 不会建立 （Actions 页面为空），也不会执行脚本。因此添加了 on-push 触发器，这样编辑一次文件之后可以正确的生成 GitHub Actions，触发器也可以正确触发。

- GitHub Actions 的 Schedule 触发不精确，可能有约 5~10 分钟的延迟。

- 重复的 Lego Batman Trilogy 领取提示，更新 Claimer 脚本后修复了。
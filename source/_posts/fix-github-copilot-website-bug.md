---
title: 使用 AdGuard 插件移除 GitHub Copilot 网页版的顶部空白
author: MC_XiaoHei
---

GitHub Copilot 的网页版本有一个很烦人的 bug，就是在顶部有一个很大的空白，等了很久也没修，故有此文。

先来看看之前的网页 bug：
![修复前](/img/fix-github-copilot-website-bug/before.png)

经过开发者工具可以很清楚地看出来，这个空白是由一个奇怪的 `div` 元素引起的，而正好 AdGuard 插件为我们提供了在指定页面移除元素的功能，可以利用这个功能来移除这个空白。

首先，我们需要打开 AdGuard 插件的主页面，确保显示 `github.com 保护已开启`，然后点击右上角的设置按钮，进入设置页面。

![AdGuard 插件主页面](/img/fix-github-copilot-website-bug/adguard-main.png)

然后点击 `用户过滤器` 选项卡，添加如下自定义规则，点击保存即可。

```adguard-rule
github.com/copilot##body > div:nth-child(1)
```

![修改拦截规则](/img/fix-github-copilot-website-bug/change-rule.png)

{% note success %}

这个规则按理说是不会对网页的其他部分产生影响的，因为这个 `div` 元素是网页的第一个子元素，所以这个规则只会删除这个 `div` 元素。

并且我们指定了仅在 `github.com/copilot` 页面生效，所以应该不会对其他页面产生影响。

{% endnote %}

{% note danger %}

这个规则是根据网页的结构来的，如果网页结构发生变化，或者 GitHub 把这个 bug 修了，这个规则可能会失效，甚至删除不应该被删除的元素。

如果失效，则需要自行前往用户过滤器页面删除这一条规则。

{% endnote %}

此时回到 GitHub Copilot 的网页版，刷新页面，顶部的空白就消失了。
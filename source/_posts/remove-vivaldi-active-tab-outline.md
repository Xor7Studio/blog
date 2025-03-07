---
title: 删除 Vivaldi 浏览器激活标签的图标边框
author: MC_XiaoHei
---

Vivaldi 浏览器在暗色模式下会为激活的标签页图标添加白色边框，而这个边框有的时候甚至会进入图标内部，破坏图标。

寻寻觅觅后找到了解决办法，在这里记录一下。

先来看看修复前的效果：

![修复前](../img/remove-vivaldi-active-tab-outline/old.png)

那么如何修复呢？

1. 打开 Vivaldi 浏览器的数据目录，一般在 `C:\Users\你的用户名\AppData\Local\Vivaldi\User Data`
2. 打开（如果没有就创建） `UserCSS` 目录（理论上名字不重要，但我只测试了这一种）。
3. 打开（如果没有就创建） `custom.css` 文件
4. 在 `custom.css` 文件中添加如下内容并保存文件：

    ```css
    .theme-dark .favicon:not(.svg) {
         filter: none !important;
    }
    ```

5. 打开 `vivaldi://experiments`，启用 `Allow for using CSS modifications` 实验功能
6. 重启 Vivaldi 浏览器
7. 打开设置 > 外观 > 自定义外观模组，选择刚才的 `UserCSS` 文件夹
8. 重启 Vivaldi 浏览器
9. Enjoy！

> 原解决办法来自 [Vivaldi 论坛](https://forum.vivaldi.net/topic/67942/removing-white-glow-outline-on-tab-icons)
> 

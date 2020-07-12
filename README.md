<h1 align="center">MDN Language Helper</h1>
浏览 MDN 时，有些链接仍会跳转到英文页面，导致经常需要手动切换语言？使用该脚本来自动解决吧！

若当前 MDN 页面语言非中文，则自动跳转到对应中文页面。

*计划中： 多语言支持。

*In plan: Multi-language support.

## 灵感
浏览 MDN 的时候，虽然设置了语言为中文，但是部分页面内的链接依然是链接到英文版页面的。为了解决反复切换语言的麻烦，故写了这个简单的 js 脚本。

## 兼容性
适用于 Tampermonkey Chrome 扩展，暂未测试其他同类扩展的兼容性。

## 使用方法：
1. 安装 Tampermonkey Chrome 扩展，此扩展可以为浏览器添加脚本运行能力。
2. 在扩展中选择“添加新脚本”，将 app.js 中的代码全部复制到编辑器中，直接使用 ```ctrl + S``` 快捷键保存即可。
3. 确认该脚本已启用。

## 其他说明：
脚本代码包含了仅在 MDN 相关页面上运行的设置，不需要额外配置。

目前脚本没有添加自动更新功能。

## 已知问题：
1. 由于指向页内标题的参数会随着语言的变化而变化，故仅通过当前方法改变页面语言时，# 后面的参数可能失效，不一定能跳转到原有语言指向的标题。

## 更新内容：
### 0.1.1
- 第一个版本，实现从非中文页面跳转到中文页面的基本功能。
### 0.2.0
- 去除了 # 后面的参数，因为指向页内标题的参数会随着语言的变化而变化，故目前强行去除了该参数。
### 0.3.0
- *开发中： 为 MDN 页面添加与页面顶部已有的下拉列表样式相同的下拉列表，以为添加后续功能做准备，包括切换语言，添加 MDN 浏览器搜索快捷键等。
- 取消去除 # 后面的参数的功能，因为即使无法导航到指定位置，参数本身也有含义。
- 脚本注入时机延迟到页面完全加载后，因为此时才能在 DOM 指定位置插入元素。但是脚本注入时机延后会导致跳转页面功能变慢。
### 0.3.1
- 脚本注入时机提前，目前尚不清楚每种注入时机的具体效果。
- 添加下拉菜单项目，但尚不具备具体功能。
### 0.3.2
- 若使用后退按钮或者从历史记录打开非目标语言页面，则不自动跳转。
- 修复了下拉菜单的显示，因 MDN 网站样式更新导致添加的下拉菜单失效。
- 暂时隐藏添加的下拉菜单，因暂无功能，且未确定如何添加不会过度干扰视觉的选项按钮。
# 搜索引擎语法

## 语法

| 名字 | 关键字 | 描述 | 范围 |示例 |
| :-----| :----: | :---- |:----: |:---- |
| 双引号 | "" | 完全匹配搜索 |百度/Google |"关键字" |
| 减号 | - | 搜索不包含减号后面的词 |百度/Google | -关键字 |
| 指定类型 | filetype: | 指定搜索特定文件格式 |百度/Google | filetype:ppt 关键字 |
| inurl | inurl: | 搜索查询词出现在url 中 |百度/Google | inurl:关键字 |
| intitle | intitle: | 页面title 中包含关键词 |百度/Google | intitle:关键字 |
| site | site: | 搜索网站 | 百度/Google | site:taobao.com 商品 |
| allintitle | allintitle: | 页面标题中包含多组关键词的文件 |百度/Google | allintitle:SEO 关键字 |
| related | related: | 与某个网站有关联的页面 |Google | related: http://taobao.com |
| inanchor | inanchor: | 导入链接锚文字中包含搜索词 |Google | inanchor:关键字 |
| 星号 | * | 搜索通配符 |Google | \*关键字\* |

## 组合使用
查询 xxx.com 文件类型为 doc 内容为 pass -> *site:xxx.com filtype:doc intext:pass*

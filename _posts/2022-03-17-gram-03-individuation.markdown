---
layout: post
title:  "03. 个性化"
date:   2022-03-17 12:13:03
category: 分类a
excerpt: 简介个性化
author: dave
---

# 一. 模板

## 1. 简介

Jekyll 使用 Liquid 模板语言，支持所有标准的 Liquid 标签和过滤器。Jekyll 甚至增加了几个过滤器和标签，方便使用。

## 2. [过滤器](http://jekyllcn.com/docs/templates/)

1. 日期格式化
2. 检索
3. 判断
4. 分组

## 3. 标签

### i. 引用 include 和 include_relative

{% include p.html %}

也可以引用非_includes目录

{% include_relative test/p.html %}



<p>本页一共 {{ page.content | number_of_words }} 个字</p>

### ii. 代码高亮 highlight

Rouge 在 Jekyll 3 及以上版本是默认高亮脚本

另外，你也可以使用 Pygments 实现代码高亮。要使用 Pygments，你必须在你系统上安装 Python，安装 pygment.rb gem 并在配置文件中设置 highlighter 为 pygments。Pygments 支持超过 一百种语言。

{% highlight ruby %}
def foo
puts 'foo'
end
{% endhighlight %}

{% highlight ruby linenos %}
@SpringBootApplication
public class Sp04SecurityApplication {

    public static void main(String[] args) {
        SpringApplication.run(Sp04SecurityApplication.class, args);
    }

}
{% endhighlight %}

- 如果使用linenos ，可能还需要在 syntax.css 加入 .lineno 样式。


## 4. 链接

### i. link

[grammer-01]({% link _posts/2022-03-17-gram-01-menu-cl.markdown %})

### ii. post_url 不需要后缀名

[grammer-02]({% post_url 2022-03-17-gram-02-blogscontent %})

### iii. Gist

- 不知道是啥

# 二. [永久链接](http://jekyllcn.com/docs/permalinks/)

默认配置为 date

永久链接的模板用以冒号为前缀的关键词标记动态内容，比如 date 代表 /:categories/:year/:month/:day/:title.html。

## 1. 模板变量

| 变量 | 描述 |
|:--------|:-------:|
| year   | 文章文件名中的年份，格式如 `2013`   |
| month   | 文章文件名中的月份，格式如 `01`   |
| i_month   | 文章文件名中的月份，不包含首位的零，格式如 `1`   |
| categories   | 文章类型。如果一篇文章有多个类型，Jekyll 会创建一个目录（例如，/category1/category2）。Jekyll 也可以自动解析 URLs 中的双斜线 `//`，所以如果当前文章没有设定类型，则忽略该项。   |

## 2. 内建永久连接类型

| 永久链接类型 | URL 模板 |
|:--------|:-------:|
| date   | /:categories/:year/:month/:day/:title.html   |

## 3. 页面（Pages） 和集合（collections）

permalink，可以在页面或者文件头重写覆盖

## 4. [永久模板举例](http://jekyllcn.com/docs/permalinks/#%E6%B0%B8%E4%B9%85%E9%93%BE%E6%8E%A5%E6%A8%A1%E6%9D%BF%E4%B8%BE%E4%BE%8B)

| 永久链接类型 | 对应的永久链接 URL |
|:--------|:-------:|
| 没有配置或 permalink: date   | /2009/04/29/slap-chop.html   |

## 其他中间件 Apache / nginx

# 三. 分页功能

## 1. 环境

1. gem 插件
~~~
gem install jekyll-paginate
~~~
2. _config.yml

{% highlight ruby %}

- 开启分页功能
paginate: 2
- 还需要配置 
paginate_path: "/blog/page:num"
- 此处配置容易出错，如果不加上 /, 后续 site.paginate_path 处理数据时会在当前url追加地址，造成页码混乱

{% endhighlight %}

3. Gemfile
~~~
gem 'jekyll-paginate', group: :jekyll_plugins
~~~
4. 使用
~~~
1. 还没看出来咋用
2. 删除原来的index.md
3. 用示例代码防御index.html
4. build
~~~
5. 返回首页会出错
~~~
官方给的两个例子都有bug

~~~


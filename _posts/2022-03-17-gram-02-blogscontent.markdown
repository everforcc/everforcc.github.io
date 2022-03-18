---
layout: post
title:  "02. 如何写博客"
date:   2022-03-17 12:13:02
category: 分类a
excerpt: 基础博客内容
author: dave
---

[TOC]

## 一. 头信息

1. loyout 
2. permalink 自定义路径 permalink: /user/defined/blogs.html
3. published: false 设置为false则不生成
4. excerpt: 自定义摘要
5. date:   2022-03-17 18:55:46 +0800

### 1. 目录结构

布局
~~~
├── _layouts
│   ├── default.html
│   ├── home.html
│   ├── page.html
│   └── post.html
~~~

## 二. 博客内容

### 1. 文章标题

- 年-月-日-标题.MARKUP

### 2. 内容格式

- 引用图片

![gitee的图片](https://gitee.com/MyYukino/media/raw/master/picture/%E9%9D%A2%E5%8C%85.jpg)

… 你可以直接 [下载图片](https://gitee.com/MyYukino/media/raw/master/picture/%E9%9D%A2%E5%8C%85.jpg).

### 3. 文章目录，最外层

- url,tile,摘要， 首页有代码测试
- 全局设置

~~~
你也可以在 _config.yml 中全局声明 excerpt_separator。
完全禁止掉可以将 excerpt_separator 设置成 ""。
~~~

### 4. 高亮代码片段,行数

- linenos 可以显示行数

{% highlight ruby linenos %}
def show
@widget = Widget(params[:id])
respond_to do |format|
format.html # show.html.erb
format.json { render json: @widget }
end
end
{% endhighlight %}

## 三. 草稿

- 目录
~~~
|-- _drafts/
|   |-- a-draft-post.md
~~~
~~~
为了预览你拥有草稿的网站，运行带有 --drafts 配置选项的 jekyll serve 或者 jekyll build。此两种方法皆会将该草稿的修改时间赋值给草稿文章，作为其发布日期，所以你将看到当前编辑的草稿文章作为最新文章被生成。
~~~

## 四. 创建页面

- 目录
- 增加一个新页面的最简单方法就是把给 HTML 文件起一个适当的名字并放在根目录下。一般来说，一个站点下通常会有：主页 (homepage), 关于 (about), 和一个联系 (contact) 页。根目录下的文件结构和对应生成的 URL 会是下面的样子
~~~
.
|-- _config.yml
|-- _includes/
|-- _layouts/
|-- _posts/
|-- _site/
|-- about.html    # => http://example.com/about.html
|-- index.html    # => http://example.com/
|-- other.md      # => http://example.com/other.html
└── contact.html  # => http://example.com/contact.html
~~~
- 或者
~~~
├── contact/
|   └── index.html  # => http://example.com/contact/
~~~

## 五. [静态文件](http://jekyllcn.com/docs/static-files/)

- 暂时还没用

## 六. [常用变量](http://jekyllcn.com/docs/variables/)

- [ ] 全局变量
- [ ] 全站变量
- [ ] 页面变量
- [ ] 分页器

## 七. 

## 八. 数据文件

1. 从csv读取

<ul>
{% for member in site.data.members-csv %}
  <li>
    <a href="https://github.com/{{ member.github }}">
      {{ member.name }}
    </a>
  </li>
{% endfor %}
</ul>

2. 从yml读取

<ul>
{% for member in site.data.members-yml %}
  <li>
    <a href="https://github.com/{{ member.github }}">
      {{ member.name }}
    </a>
  </li>
{% endfor %}
</ul>

3. _data子目录

- 读取文件夹下的所有数据，从目前来看结构要相同
<ul>
{% for org_hash in site.data.orgs %}
{% assign org = org_hash[1] %}
  <li>
    <a href="https://github.com/{{ org.username }}">
      {{ org.name }}
    </a>
    ({{ org.members | size }} members)
  </li>
{% endfor %}
</ul>

4. 访问特定的数据

- 如果ref不写前缀，默认当前路径

{% assign author = site.data.people[page.author] %}
<a rel="author"
href="https://github.com/{{ author.github }}"
title="{{ author.name }}">
{{ author.name }}
</a>

## 九. 资源

- 支持其他的资源

## 十. 博客迁移

- 从其他博客迁移过来

## 三. 

## ？. Kramdown 语法

- [官方文档](https://kramdown.gettalong.org/quickref.html)

1. 1标题

<p>由于jekyll用的是Kramdown,在此记录下常见语法</p>

~~~
标题 
# 一级
###### 六级
~~~
2. 2指定标头ID

没看明白什么意思

###### I can help you  {#head_1}

3. 3表格

| Header1 | Header2 | Header3 |
|:--------|:-------:|--------:|
| cell1   | cell2   | cell3   |
| cell4   | cell5   | cell6   |
|----
| cell1   | cell2   | cell3   |
| cell4   | cell5   | cell6   |
|=====
| Foot1   | Foot2   | Foot3
{: rules="groups"}

4. 4 if和code


{% highlight ruby %}
def print_hi(name)
puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

{% if jekyll.environment == "production" %}
production
{% endif %}

{% if jekyll.environment == "development" %}
环境默认为: development
{% endif %}

5. 5其他的参考文档，需要了再记下来

## 四. 常见问题

### 1. 如何支持 [TOC] 标签

  普通文字 `被包围起来的文字` directory. 
  
文本中的链接可以放到下面处理 [Jekyll docs][jekyll-docs] 

File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/


HTML 内代码：
<h6 id="head_1">I can help you</h6>
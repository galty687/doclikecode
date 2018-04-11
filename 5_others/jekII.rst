=============================
Markdown+Jekyll+Github Pages
=============================

Jekyll帮助页面示例:

* `GitHub Official Teaching Materials <https://services.github.com/workflow-consultation>`_ , `源代码 <https://github.com/github/training-kit>`_
* `beegit帮助文档 <http://help.beegit.com>`_ , `源代码 <https://github.com/beegit/help.beegit.com>`_
* `circleci帮助文档 <https://circleci.com/docs/2.0/>`_ , `源代码 <https://github.com/circleci/circleci-docs>`_

行业实践：

* `开源项目openstack的文档 https://docs.openstack.org/doc-contrib-guide/index.html`_

课程演示任务：

Github Pages 托管静态页面
=====================================
#. 下载CATTP平台中的个人单页面压缩包
#. 在Github中新建一个repo
#. 将html页面托管在repo中

漂亮的单页面帮助文档

#. https://pages.github.com/#user-site

其他参考教程：`Creating and Hosting a Personal Site on GitHub <http://jmcglone.com/guides/github-pages/>`_

具体步骤：
-------------------
#. 在Github上创建新的repo，例如命名为 demo-single-page
#. 通过Github Desktop同步到本地文件夹 demo-single-page
#. 将从CATTP平台上下载的单页面网站，复制到本地文件夹 demo-single-page 中，并push到远程repo




使用Jekyll Now迅速部署自己的博客
=============================================

#. Fork Jekyll-now主题，并将repo改为 yourusername.github.io
#. 在_config.yml中配置自己的个人信息 
#. 修改jekyll的 `主题 <https://jekyll-themes.com>`_

* 更多帮助信息：https://www.smashingmagazine.com/2016/02/content-modeling-with-jekyll/
* Jekyll Documentation Theme: http://idratherbewriting.com/documentation-theme-jekyll//#

完整版jekyll安装
=============================

#. 安装jekyll环境：sudo gem install jekyll bundler
#. 创建新博客：jekyll new my-awesome-site
#. 启动网站。进入网站文件夹后，运行：bundle exec jekyll serve
#. 浏览网站。localhost:4000

更多帮助信息：https://jekyllrb.com


添加内容并发布新网站
==============================
#. 使用Markdown语法创建任意内容，按照 YYYY-MM-DD-Title 的格式命名
#. 将上方创建的Markdown文件，保存在 my-awesome-site/_posts中
#. 在Terminal中运行 jekyll build，jekyll将发布网站，并将静态内容存储在 _site 文件夹中






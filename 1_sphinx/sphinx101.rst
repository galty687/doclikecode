=====================
Sphinx快速入门
=====================
:date: 2018/04/12
:author: 高志军

Sphinx是一个静态网页发布工具，可将rST和md文件，发布为各类常见的用户帮助如联机帮助，用户手册等。


安装Sphinx 
=====================

Mac系统
----------------
在Terminal中运行如下代码

    .. code-block:: python

        pip install Sphinx



Windows系统
------------------
#. 需要首先安装pip，可参考 `pip <http://pip-cn.readthedocs.io/en/latest/installing.html>`_。
#. 运行如下代码

    .. code-block :: python

        pip install Sphinx



快速新建项目（以Mac系统为例，Window系统类似）
======================================================
#. 在桌面上创建一个文件夹，并命名为 *sphinx-demo*
#. 在Terminal中浏览至上述文件夹，并运行命令： ``sphinx-quickstart``
#. 在对话框式的选择中，Y/N的选项，选Y；如果询问配置，直接复制[]中的内容，如[.rst]，则填写.rst
#. 新建成功后，则会得到如图所示的文件夹结构

::

    .
    ├── build
    ├── make.bat
    ├── Makefile
    └── source
        ├── conf.py
        ├── index.rst
        ├── _static
        └── _templates





往项目中添加内容
============================
#. 浏览至 *source* 文件夹，并在其根目录下创建新文件夹demo
#. 在上方 *demo* 文件夹中，新建test.rst文件，并在其中输入如下内容：

::

        =======================
        这是Sphinx的测试
        =======================
        我爱学习Sphinx

#. 打开source文件中的 index.rst，将test.rst的文件添加至目录中，具体如下：

    .. image:: images/add-toctree.png
        :height: 200px
        :width: 400 px
        :alt: 添加至首页目录
        
        
#. 在Terminal中运行编译命令 ``sphinx-build -b html source build``

#. 编译成功的话，在 *build* 文件夹中则有刚才发布的网站



修改主题
===================
#. 打开 *source* 文件夹中的conf.py，并找到主题配置行 html_theme = 'alabaster'
#. 从内置主题中挑选需要的主题，如 bizstyle，将其改为 html_theme = 'bizstyle'
#. 重新运行发布命令后，则可得到新主题的样式的帮助文档

.. note::
    Sphinx内置主题的样式可见：http://www.sphinx-doc.org/en/master/theming.html#using-a-theme。还可以安装其他主题，或者按照需要制作自己的主题。




安装ReadtheDoc同款主题
===========================

如果喜欢 `readthedocs.org <https://docs.readthedocs.io/en/latest/getting_started.html>`_ 的主题，可以按照如下方式安装

.. code-block:: python

    pip install sphinx_rtd_theme

安装之后，再按照上述步骤，将 ``conf.py`` 中的主题行，修改为html_theme = 'sphinx_rtd_theme'，再运行 ``sphinx-build`` 命令重新发布即可。

实现帮助文档公网可访问
==========================
执行 ``sphinx-build`` 命令后，sphinx会将rst的内容，发布为静态网站。只需将 *build* 文件夹中的文件，托管至github，即可实现公网访问。


由ReadtheDocs执行发布命令
===============================
每次更新后，都需执行 ``sphinx-build`` 命令，并重新上传至Github，较为麻烦。这个工作可以由ReadTheDocs平台自动化完成。

#. 注册ReadTheDocs账号
#. 将Github账号关联到ReadtheDocs
#. 将source文件中的内容，上传至github中的某个repo中
#. 选择github的相应ropo，自动创建webhook
#. 后续每次源文件内容有变化后，ReadtheDoc均可以自动发布最新的版本

更多内容参见ReadtheDocs官方文档：https://docs.readthedocs.io/en/latest/getting_started.html

**下次课内容**

* reStructedText 
* 自定义主题
* 制作主题
* 发布为PDF等其他样式

预习：

* HTML，CSS
* Jinjia 模板语言

**参考资料**

[Sphinx官方教程]: http://www.sphinx-doc.org/en/master/usage/quickstart.html


演示本地修改，自动发布。

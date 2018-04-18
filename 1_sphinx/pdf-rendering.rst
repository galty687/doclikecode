==================
使用rinoh输出 PDF
==================

Sphinx输出为PDF有多种方式，例如依赖LaTex技术，现将rst转为latex，在转为PDF。现在也有多种其他方案，如Rinoh或rst2pdf等。本节将主要介绍rinoh插件。。


rinoh插件安装
==================
首先通过pip，安装依赖库：

* docutils
* recommonmark ，

如果已经有的话，在Terminal中直接运行 ``pip install rinohtype``，即可安装

发布单个PDF
==================
#. 在Termina中浏览至桌面上source文件夹，
#. 运行：``rinoh index.rst`` 即可发布为PDF

发布项目
====================

配置conf.py
-------------------
需要在conf.py中对 ``latex_elements``进行配置

::

    latex_elements = {
        # The paper size ('letterpaper' or 'a4paper').
        'papersize': 'letterpaper',
        # 'papersize': 'letterpaper',

        # The font size ('10pt', '11pt' or '12pt').
        #
        # 'pointsize': '10pt',

        # Additional stuff for the LaTeX preamble.
        #
        # 'preamble': '',

        # Latex figure (float) alignment
        #
        # 'figure_align': 'htbp',
    }

配置后，需要增加

::

    # Configure Rinoh documents

    rinoh_documents = [('index',    # top-level file (index.rst)
                        'target', # output (target.pdf)
                        'Sphinx Quickstart', # document title
                        'Zhijun Gao')] # document author


配置后，运行：``sphinx-build -b rinoh source build2``



参考资料：

[1]. https://github.com/brechtm/rinohtype
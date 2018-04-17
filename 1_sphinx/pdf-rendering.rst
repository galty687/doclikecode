==================
输出为 PDF
==================

Sphinx输出为PDF有多种方式，例如依赖LaTex技术，现将rst转为latex，在转为PDF。现在也有多种其他方案，如Rinoh或rst2pdf等。本节将主要介绍rinoh插件。


rinoh插件安装
==================
依赖：docutils 和 recommonmark ，可以通过pip安装。

如果已经有的话，在Terminal中运行 ``pip install rinohtype``

发布
==================
#. 在Termina中浏览至桌面上source文件夹，
#. 运行：``rinoh index.rst`` 即可发布为PDF
==================
输出为 PDF
==================

Sphinx输出为PDF有多种方式，例如依赖LaTex技术，现将rst转为latex，在转为PDF。现在也有多种其他方案，如Rinoh或rst2pdf等。本节将主要介绍rinoh插件。


rinoh插件安装
==================
首先通过pip，安装依赖库：

* docutils
* recommonmark ，

如果已经有的话，在Terminal中直接运行 ``pip install rinohtype``，即可安装

发布 PDF
==================
#. 在Termina中浏览至桌面上source文件夹，
#. 运行：``rinoh index.rst`` 即可发布为PDF


参考资料：

[1]. https://github.com/brechtm/rinohtype
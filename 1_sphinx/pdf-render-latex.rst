===================
使用LaTex输出PDF
===================

前提条件
===========
首先安装MacText，安装步骤： ``brew cask install mactex``


基本步骤：
===========


#. 首先将sphinx 发布为 latex。`` sphinx-build -b latex source target``
#. 运行 ``pdflatex target`` 将 latex发布为pd使用LaTex发布PDF


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


使用XeLaTex
=================


XeTeX 也是TEX排版的一种，支持Unicode而且也支持现代字体技术如，OpenType (OTF), TrueType (TTF), Graphite, and Apple Advanced Typography (AAT)。对应的编译器为 xetex 和 xelatex。

编译中文是，在conf.py中的做如下设置：

 .. code-block:: python

    latex_elements = {
        'papersize' : 'a4paper',
        'utf8extra' : '',
        'inputenc'  : '',
        'babel'     : r'''\usepackage[english]{babel}''',
        'preamble' : r'''
        \usepackage{ctex}
        ''',
    }


#. make latex
#. 使用Texshop 打开进行上一步编译得到 *.tex文件，选择 **XeLaTex** 引擎
#. 点击Typeset 即可得到中文版。

因为 readthedocs 上只有pdflatex引擎，如果需要同时在readthedocs和本地化都能顺利编译中文pdf的话，可以在 conf.py中添加如下配置：

.. code-block:: python

    import os

    on_rtd = os.environ.get('READTHEDOCS', None) == 'True'
    if on_rtd:
        latex_elements = {
        # The paper size ('letterpaper' or 'a4paper').
        #'papersize': 'letterpaper',
        # The font size ('10pt', '11pt' or '12pt').
        #'pointsize': '10pt',
        # Additional stuff for the LaTeX preamble.
        'preamble': r'''
        \hypersetup{unicode=true}
        \usepackage{CJKutf8}
        \DeclareUnicodeCharacter{00A0}{\nobreakspace}
        \DeclareUnicodeCharacter{2203}{\ensuremath{\exists}}
        \DeclareUnicodeCharacter{2200}{\ensuremath{\forall}}
        \DeclareUnicodeCharacter{2286}{\ensuremath{\subseteq}}
        \DeclareUnicodeCharacter{2713}{x}
        \DeclareUnicodeCharacter{27FA}{\ensuremath{\Longleftrightarrow}}
        \DeclareUnicodeCharacter{221A}{\ensuremath{\sqrt{}}}
        \DeclareUnicodeCharacter{221B}{\ensuremath{\sqrt[3]{}}}
        \DeclareUnicodeCharacter{2295}{\ensuremath{\oplus}}
        \DeclareUnicodeCharacter{2297}{\ensuremath{\otimes}}
        \begin{CJK}{UTF8}{gbsn}
        \AtEndDocument{\end{CJK}}
        ''',
        }
    else:
        latex_elements = {
            'papersize' : 'a4paper',
            'utf8extra' : '',
            'inputenc'  : '',
            'babel'     : r'''\usepackage[english]{babel}''',
            'preamble' : r'''
            \usepackage{ctex}
            ''',
        }



rST和latex的类比
===================

 .. code-block:: rest

	=================================================
	Cartesian closed categories and the price of eggs
	=================================================

	:author: Jane Doe
	:date: September 1994

	My First Chapter
	================

	Hello world!



.. code-block:: latex

	\documentclass{article}
	\title{Cartesian closed categories and the price of eggs}
	\author{Jane Doe}
	\date{September 1994}
	\begin{document}
	\maketitle
	\section{My First Chapter}
	Hello world!
	\end{document}

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

::

    latex_engine = 'xelatex'
    latex_elements = {
        # The paper size ('letterpaper' or 'a4paper').
        #
        # 'papersize': 'letterpaper',

        # The font size ('10pt', '11pt' or '12pt').
        #
        # 'pointsize': '10pt',

        'fncychap' : '',

        # Additional stuff for the LaTeX preamble.
        #
        'preamble': r'''\usepackage{ctex}
        ''',

        # Latex figure (float) alignment
        #
        # 'figure_align': 'htbp',
    }

执行任务： ``make latexpdf``
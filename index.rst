.. Docs like Code documentation master file, created by
   sphinx-quickstart on Mon Apr  9 17:22:35 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

基于Sphinx的技术文档开发教程
==========================================
本书将介绍一种轻量级的文档解决方案，所用工具均为成熟的开源技术。阅读本书后，读者可以用本书的方法，轻松为公司的产品或服务提供所需的帮助文档。

**适合读者：**

* 软件文档项目团队
* 小型写作团队

本书用于《技术传播方法》课程的教学，因为服务于技术写作课程的教学，本书将采用当前流行的 *Doc like Code* 的模式进行写作。

所用的工具如下：

1. 内容写作。采用轻量级的标记语言：`reStructuredText <http://www.sphinx-doc.org/en/master/rest.html#rst-primer>`_
#. 文档发布工具。`Sphinx <http://www.sphinx-doc.org/en/master/index.html>`_
#. 协同与版本控制。`github <http://github.com>`_
#. 文档托管。`Read the Docs <http://readthedocs.org>`_
#. 写作工具。`MS Visual Studio Code <https://code.visualstudio.com>`_

本课程选课同学将按照技术写作的流程，参与到教程的写作和审校工作中。

.. toctree::
   :maxdepth: 2
   :caption: 第一章：快速上手

   0_Introduction/intro.rst
   0_Introduction/advantages.rst
   0_Introduction/sphinx-projects.rst


.. toctree::
   :maxdepth: 2
   :caption: 第二章：Sphinx

   1_sphinx/sphinx101.rst
   1_sphinx/pdf-rendering.rst
   1_sphinx/pdf-render-latex.rst

.. toctree::
   :maxdepth: 2
   :caption: 第三章：reStructuredText

   2_rst/rst101.rst
   2_rst/rst-publish.rst
   2_rst/rst-quick-ref.md

   
.. toctree::
    :maxdepth: 2
    :caption: 第四章：Sphinx主题

    4_theming/rtd-theme
    4_theming/jinja

.. toctree::
   :maxdepth: 2
   :caption: 第四章：Github


.. toctree::
   :maxdepth: 2
   :caption: 第五章：Read the Docs

   4_readthedoc/

.. toctree::
   :maxdepth: 2
   :caption: 其他工具链

   5_others/jekII.rst
   5_others/jekyll-theme



索引和表格
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

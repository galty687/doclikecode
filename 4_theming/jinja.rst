================
Jinja 模板语言
================


Jinjia是Python的类库，因为Django框架将其用作模板语言，因为有很大的知名度。

安装：``pip install Jinja2``

快速示例：

.. code-block:: python

    from jinja2 import Template
    template = Template('Hello {{ name }}!')
    template.render(name='John Doe')



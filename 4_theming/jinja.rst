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


极简模板

.. code-block:: html

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <title>My Webpage</title>
    </head>
    <body>
        <ul id="navigation">
        {% for item in navigation %}
            <li><a href="{{ item.href }}">{{ item.caption }}</a></li>
        {% endfor %}
        </ul>

        <h1>My Webpage</h1>
        {{ a_variable }}

        {# a comment #}
    </body>
    </html>

代码含义：

* {% ... %} for Statements
* {{ ... }} for Expressions to print to the template output
* {# ... #} for Comments not included in the template output
* #  ... ## for Line Statements    


参考资料：

[1]. http://jinja.pocoo.org


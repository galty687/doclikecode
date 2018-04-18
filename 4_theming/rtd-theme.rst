================
rtd theme 配置
================

rtd 主题由Read the Doc团队开发，主题美观大方。本小节将以此主题为例，说明主题如何自定义。

主题配置
==================
主题的配置文件在 ``sphinx_rtd_theme/theme.conf`` 文件中，默认配置如下：

::

    [theme]
    inherit = basic
    stylesheet = css/theme.css

    [options]
    typekit_id = hiw1hhg
    analytics_id =
    sticky_navigation = False
    logo_only =
    collapse_navigation = False
    display_version = True
    navigation_depth = 4
    prev_next_buttons_location = bottom
    canonical_url =


基本选项含义：

* ``analytics_id`` 字符串。配置 Google Analytics ID 可以追踪网站访问情况。
* ``display_version`` 布尔值。配置是否显示版本号。

导航栏选项：

* ``collapse_navigation`` 布尔值。启用后，不在导航栏中显示 +。
* ``navigation_depth`` 整数。最大深度为4层，设置为 -1 表示不限制深度。

更多说明，可见 `官方文档 <https://sphinx-rtd-theme.readthedocs.io/en/latest/configuring.html>`_


PDF输出：http://media.readthedocs.org/pdf/doclikecode/latest/doclikecode.pdf
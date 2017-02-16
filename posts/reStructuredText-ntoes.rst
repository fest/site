.. title: reStructuredText Notes
.. slug: reStructuredText-notes
.. date: 2017-02-12 21:06:35 UTC+08:00
.. tags: python
.. category: notes
.. link:
.. description:
.. type: text

参考：

1. `reStructuredText Markup Specification`_

2. `reStructuredText Primer`_

3. `reStructuredText Quick Reference`_

.. TEASER_END

章节结构
==========

- 常用符号：

  ``= - ` : . ' " ~ ^ _ * + #``

- 所有可用符号：

  ``! " # $ % & ' ( ) * + , - . / : ; < = > ? @ [ \ ] ^ _ ` { | } ~``

Transition 
------------

Transition 符号由4个或以上 `章节结构`_ 里允许用的符号组成，都会被渲染成水平线。如下面的水平线是由 ``####`` 渲染成的。

####
  
常用语法
==========

+----------------------------------------------------------+----------------------------------------------------------+
| ::                                                       |                                                          |
|                                                          |                                                          |
|    *倾斜*                                                | *倾斜*                                                   |
|                                                          |                                                          |
|    **加粗**                                              | **加粗**                                                 |
|                                                          |                                                          |
|    ``inline literal``                                    | ``inline literal``                                       |
|                                                          |                                                          |
|    注释由两个点加空格起头，渲染后不会显示：              | 注释由两个点加空格起头，渲染后不会显示：                 |
|                                                          |                                                          |
|    .. 这里是注释，将不会被显示。                         | .. 这里是注释，将不会被显示。                            |
+----------------------------------------------------------+----------------------------------------------------------+
| ::                                                       |                                                          |
|                                                          |                                                          |
|    - 直接使用网址，以http或https起头：                   | - 直接使用网址，以http或https起头：                      |
|                                                          |                                                          |
|      http://yongchen.org                                 |   http://yongchen.org                                    |
|                                                          |                                                          |
|    - 用文字表示链接 I：                                  | - 用文字表示链接 I：                                     |
|                                                          |                                                          |
|      `my site <http://yongchen.org>`_                    |   `my site <http://yongchen.org>`_                       |
|                                                          |                                                          |
|    - 用文字表示链接 II：                                 | - 用文字表示链接 II：                                    |
|                                                          |                                                          |
|      `my site`_                                          |   `my site`_                                             |
|                                                          |                                                          |
|      .. _my site: http://yongchen.org                    |   .. _my site: http://yongchen.org                       |
|                                                          |                                                          |
|    - 所有的章节标题都可以被引用：                        | - 所有的章节标题都可以被引用：                           |
|                                                          |                                                          |
|      `章节结构`_                                         |   `章节结构`_                                            |
+----------------------------------------------------------+----------------------------------------------------------+
| ::                                                       | 文字，图片等对象的替代 (substitution) :                  |
|                                                          |                                                          |
|    The |Nikola| image is shown here.                     | The |Nikola| image is shown here.                        |
|                                                          |                                                          |
|    .. |Nikola| image:: /images/nikola.png                | .. |Nikola| image:: /images/nikola.png                   |
|                :align: middle                            |             :align: middle                               |
|                :width: 30 (网页中我们常用480)            |             :width: 30                                   |
+----------------------------------------------------------+----------------------------------------------------------+
| ::                                                       | 脚标，下面的例子中也可以使用 # 自动计数                  |
|                                                          |                                                          |
|    footnote reference [1]_                               | footnote reference [1]_                                  |
|                                                          |                                                          |
|    .. [1] A footnote example linked to [1].              | .. [1] A footnote example linked to [1].                 |
+----------------------------------------------------------+----------------------------------------------------------+
| ::                                                       | 文献引用，和脚标用法类似。                               |
|                                                          |                                                          |
|    citation reference [CIT2002]_                         | citation reference [CIT2002]_                            |
|                                                          |                                                          |
|    .. [CIT2002] A citation example.                      | .. [CIT2002] A citation example.                         |
+----------------------------------------------------------+----------------------------------------------------------+
| ::                                                       | 使用 backslash 显示那些特殊字符。                        |
|                                                          |                                                          |
|    - \*星号*                                             | - \*星号*                                                |
|                                                          |                                                          |
|    - \``代码符号``                                       | - \``代码符号``                                          |
|                                                          |                                                          |
|    - 反斜杠 \\                                           | - 反斜杠 \\                                              |
+----------------------------------------------------------+----------------------------------------------------------+
| ::                                                       |                                                          |
|                                                          |                                                          |
|    Lists:                                                | Lists:                                                   |
|                                                          |                                                          |
|    - item 1. 第一项前和最后一项后必须各留出一空行.       | - item 1. 第一项前和最后一项后必须各留出一空行.          |
|    - item 2. List 由 "*", "+", "-" 等符号引导。          | - item 2. List 由 "*", "+", "-" 等符号引导。             |
|                                                          |                                                          |
|    - item 3. 中间各项之间可留空行也可省略.               | - item 3. 中间各项之间可留空行也可省略.                  |
|                                                          |                                                          |
|      1. nested item 1. 此前又须留出一空行。数字型的list接|   1. nested item 1. 此前又须留出一空行。数字型接         |
|         受这几种格式：                                   |      受这几种格式：                                      |
|                                                          |                                                          |
|         a. 阿拉伯数字 1, 2, 3 ...                        |      a. 阿拉伯数字 1, 2, 3 ...                           |
|         #. 大写或小写字母 A, B, ..., Z. a, b, ..., z.    |      #. 大写或小写字母 A, B, ..., Z. a, b, ..., z.       |
|         #. 大写或小写罗马数字 I, II, ... 或 i, ii, ...   |      #. 大写或小写罗马数字 I, II, ... 或 i, ii, ...      |
|                                                          |                                                          |
|    Definition Lists: 词或变量                            | Definition Lists: 词或变量                               |
|                                                          |                                                          |
|    what                                                  | what                                                     |
|        Definition lists associate a term with a          |     Definition lists associate a term with a             |
|        definition.                                       |     definition.                                          |
|                                                          |                                                          |
|    lines : string                                        | lines : string                                           |
|        List of one-line strings without newlines.        |     List of one-line strings without newlines.           |
|                                                          |                                                          |
|    Field Lists:                                          | Field Lists:                                             |
|                                                          |                                                          |
|    :Authors:                                             | :Authors:                                                |
|        Tony J. (Tibs) Ibbs,                              |     Tony J. (Tibs) Ibbs,                                 |
|        David Goodger                                     |     David Goodger                                        |
|                                                          |                                                          |
|        (and sundry other good-natured folks)             |     (and sundry other good-natured folks)                |
|                                                          |                                                          |
|    :Version: 1.0 of 2001/08/08                           | :Version: 1.0 of 2001/08/08                              |
|                                                          |                                                          |
|    :Dedication: To my father.                            | :Dedication: To my father.                               |
|                                                          |                                                          |
|    Option Lists:                                         | Option Lists:                                            |
|                                                          |                                                          |
|    -a file    command-line option "a"                    | -a file    command-line option "a"                       |
|    --input=file    long options can also have arguments  | --input=file    long options can also have arguments     |
|    /V    DOS/VMS-style options too                       | /V    DOS/VMS-style options too                          |
+----------------------------------------------------------+----------------------------------------------------------+
| ::                                                       |                                                          |
|                                                          |                                                          |
|    Literal Blocks:                                       | Literal Blocks:                                          |
|                                                          |                                                          |
|    ::                                                    | ::                                                       |
|                                                          |                                                          |
|      Whitespace, newlines, blank lines, and all kinds of |   Whitespace, newlines, blank lines, and all kinds of    |
|      markup is preserved by literal blocks.              |   markup is preserved by literal blocks.                 |
|                                                          |                                                          |
|    Per-line quoting can also be used on unindented       | Per-line quoting can also be used on unindented          |
|    literal blocks (顶格写时每行的 ``>`` 符号不可少)::    | literal blocks (顶格写时每行的 ``>`` 符号不可少)::       |
|                                                          |                                                          |
|    > Useful for quotes from email and                    | > Useful for quotes from email and                       |
|    > for Haskell literate programming.                   | > for Haskell literate programming.                      |
|                                                          |                                                          |
|    Line Blocks: （注意渲染后的样式与普通文字一样）       | Line Blocks: （注意渲染后的样式与普通文字一样）          |
|                                                          |                                                          |
|    | Line blocks are useful for addresses,               | | Line blocks are useful for addresses,                  |
|    | verse, and adornment-free lists.                    | | verse, and adornment-free lists.                       |
|                                                          |                                                          |
|    | Each new line begins with a                         | | Each new line begins with a                            |
|    | vertical bar ("|").                                 | | vertical bar ("|").                                    |
|    |     Line breaks and initial indents                 | |     Line breaks and initial indents                    |
|    |     are preserved.                                  | |     are preserved.                                     |
|    | Continuation lines are wrapped                      | | Continuation lines are wrapped                         |
|      portions of long lines; they begin                  |   portions of long lines; they begin                     |
|      with spaces in place of vertical bars.              |   with spaces in place of vertical bars.                 |
|                                                          |                                                          |
|    Doctest Blocks: 以 ``<<<`` 打头                       | Doctest Blocks: 以 ``<<<`` 打头                          |
|                                                          |                                                          |
|    >>> print "This is a doctest block."                  | >>> print "This is a doctest block."                     |
|    This is a doctest block.                              | This is a doctest block.                                 |
+----------------------------------------------------------+----------------------------------------------------------+
| ::                                                       |   表格：                                                 |
|                                                          |                                                          |
|   +------------+------------+-----------+                |   +------------+------------+-----------+                |
|   | Header 1   | Header 2   | Header 3  |                |   | Header 1   | Header 2   | Header 3  |                |
|   +============+============+===========+                |   +============+============+===========+                |
|   | body row 1 | column 2   | column 3  |                |   | body row 1 | column 2   | column 3  |                |
|   +------------+------------+-----------+                |   +------------+------------+-----------+                |
|   | body row 2 | Cells may span columns.|                |   | body row 2 | Cells may span columns.|                |
|   +------------+------------+-----------+                |   +------------+------------+-----------+                |
|   | body row 3 | Cells may  | - Cells   |                |   | body row 3 | Cells may  | - Cells   |                |
|   +------------+ span rows. | - contain |                |   +------------+ span rows. | - contain |                |
|   | body row 4 |            | - blocks. |                |   | body row 4 |            | - blocks. |                |
|   +------------+------------+-----------+                |   +------------+------------+-----------+                |
|                                                          |                                                          |
|   =====  =====  ======                                   |   =====  =====  ======                                   |
|      Inputs     Output                                   |      Inputs     Output                                   |
|   ------------  ------                                   |   ------------  ------                                   |
|     A      B    A or B                                   |     A      B    A or B                                   |
|   =====  =====  ======                                   |   =====  =====  ======                                   |
|   False  False  False                                    |   False  False  False                                    |
|   True   False  True                                     |   True   False  True                                     |
|   False  True   True                                     |   False  True   True                                     |
|   True   True   True                                     |   True   True   True                                     |
|   =====  =====  ======                                   |   =====  =====  ======                                   |
+----------------------------------------------------------+----------------------------------------------------------+


.. _reStructuredText Markup Specification: http://docutils.sourceforge.net/docs/ref/rst/restructuredtext.html
.. _reStructuredText Primer: http://www.sphinx-doc.org/en/stable/rest.html
.. _reStructuredText Quick Reference: http://docutils.sourceforge.net/docs/user/rst/quickref.html
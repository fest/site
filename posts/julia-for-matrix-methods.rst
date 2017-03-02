.. title: Julia for Matrix Methods
.. slug: julia-for-matrix-methods
.. date: 2017-03-01 13:59:43 UTC+08:00
.. tags: julia, tutorial, mathjax
.. category: programming
.. link:
.. description:
.. type: text

.. sectnum::

.. contents::

.. TEASER_END

.. class:: alert alert-info pull-right

.. admonition:: Source

   `Introduction to Matrix Methods <http://stanford.edu/class/ee103/julia.html>`_


Introduction
==============

Basic arithmetric & mathematical functions
---------------------------------------------

- ``+``, ``-``, ``*``, ``/``, ``^`` (exponentiate), ...
- ``true``, ``false``, ``+=``, ``!=``, ``<``, ``>``, ``<=``, ``>==``, ``!(value == 4)``, ...
- ``im`` (imaginary unit), ``pi``, ``e``, ``golden``, ...
- ``exp``, ``sqrt``, ``sin``, ``rand()``, ...
- ``println(23)``, ``quit()``, ``help(sin)``, ...
- assign multiple variables (return type: Tuple): ``a,b=5,3``

  Swap two variables: ``a,b=b,a``

Ranges
--------

- ``1:5``, ``0.0:0.1:10.0``, ``linspace(0.0,10.0,11)``
- convert **Range** to **Array**: ``collect(1:5)`` or simply use ``[1:5]`` (``collect`` is much faster)

Lists
-------

List is one-dimensional array.

- create: ``my_list = ["a", 1, -0.76]``
- access: ``m_list[2]``, ``my_list[end]``, ``my_list[end-1]``
- length: ``length(my_list)``

For loops
-----------

- loop over a **Range**

  .. code:: julia

     value = 0
     for i in 1:10
       value += i
     end

- loop over a **List**

  .. code:: julia

     value = 0
     my_list = [1,2,3,4,5]
     for i in my_list
       value += i
     end

Vectors
=========

Vectors
---------

- create: ``x=[8,-4,3.5]`` or ``x=[8;-4;3.5]``

  .. math::

     \boldsymbol{x}=\left(
     \begin{array}{c}
     8\\
     -4\\
     3.5
     \end{array}
     \right)

- index: ``x[2]``, ``x[2:3]``, ``x[end]``, ``x[1:2:end]``

- block vectors

  stacked vector: ``a=[b;c]`` (Note: Both :math:`\boldsymbol{b}` and :math:`\boldsymbol{c}` are vectors, so ``a=[b,c]`` does NOT work).

  .. math::

     \boldsymbol{a}=\left(
     \begin{array}{c}
     \boldsymbol{b}\\
     \boldsymbol{c}
     \end{array}
     \right)

- mix vectors with scalars: ``a=[b; 2; c; -6]``

- list with vectors :math:`\boldsymbol{a},\boldsymbol{b},\boldsymbol{c}`: ``vector_list=[a,b,c]``

  * second vector in this list: ``vector_list[2]``
  * access an element in a vector: ``vector_list[2][3]``

- Basic functions for arrays:

  - sum of a vector: ``sum(x)``
  - mean of the entries: ``mean(x)``
  - :math:`\boldsymbol{0}_n` (vector with all entries 0): ``zeros(n)``
  - :math:`\boldsymbol{1}_n` (vector with all entries 1): ``ones(n)``

Vector operations
-------------------

- vector addition and subtraction (the arrays must have the same length): ``+``, ``-``

- scalar-vector addition: ``[2,4,8]+3``

  .. math::

     \left(
     \begin{array}{c}
     2\\
     4\\
     8\\
     \end{array}
     \right)
     + 3 =
     \left(
     \begin{array}{c}
     5\\
     7\\
     11\\
     \end{array}
     \right)

- scalar-vector multiplication: ``-2*[1,9,6]`` or ``[1,9,6]*(-2)``

  .. math::

     -2\,
     \left(
     \begin{array}{c}
     1\\
     9\\
     6\\
     \end{array}
     \right)
     =
     \left(
     \begin{array}{c}
     -2\\
     -18\\
     -12\\
     \end{array}
     \right)

- inner product :math:`\boldsymbol{a}^T\boldsymbol{b}`: ``dot(a,b)`` (:math:`\boldsymbol{a}` and :math:`\boldsymbol{b}` must have the same length)
- vecter-vecter element-wise operation: ``[2,4].*[10,20]``

Norm and distance
----------------------

- ``norm(x)``

  .. math::

     \left\|\boldsymbol{x}\right\|=\sqrt{x_1^2+x_2^2+\dots+x_n^2}

- ``norm(x-y)``

  .. math::

     \left\|\boldsymbol{x}-\boldsymbol{y}\right\|

- root mean square: ``rms(x)``

  .. math::

     \boldsymbol{x}_{\text{rms}}=\sqrt{\frac{1}{n}\left(x_1^2+x_2^2+\dots+x_n^2\right)}=\frac{\left\|\boldsymbol{x}\right\|}{\sqrt{n}}

- angle between vectors: ``angle_a_b = acos(dot(a,b)/(norm(a)*norm(b)))``

  .. math::

     \angle (\boldsymbol{a},\boldsymbol{b})=\arccos \left(\frac{\boldsymbol{a}^T\boldsymbol{b}}{\left\|\boldsymbol{a}\right\|\left\|\boldsymbol{b}\right\|} \right)


Matrices
=============

Matrics
----------

Matrices are 2D or higher dimensional arrays.

- spaces separate entries in a row; semicolons separate individual rows: ``A=[2 -4 8.2; -5.5 3.5 63]``

  .. math::

     \boldsymbol{A}=
     \left(
     \begin{array}{ccc}
     2 & -4 & 8.2\\
     -5.5 & 3.5 & 63\\
     \end{array}
     \right)

- ``A_rows, A_cols = size(A)``: returns the tuple containing the dimensions of :math:`\boldsymbol{A}`. (``A_rows`` is ``size(A)[1]``, ``A_cols`` is ``size(A)[2]``).

- block matrix: ``X=[A B; C D]`` (:math:`\boldsymbol{A}, \boldsymbol{B}, \boldsymbol{C}` and :math:`\boldsymbol{D}` are matrices)

  .. math::

     \boldsymbol{X}=
     \left(
     \begin{array}{ccc}
     \boldsymbol{A} & \boldsymbol{B}\\
     \boldsymbol{C} & \boldsymbol{D}\\
     \end{array}
     \right)

- useful matrices:

  - :math:`\boldsymbol{0}_{m \times n}` (vector with all entries :math:`0`): ``zeros(m,n)``
  - :math:`\boldsymbol{1}_{m \times n}` (vector with all entries :math:`1`): ``ones(m,n)``
  - :math:`\boldsymbol{I}_{n}` (identity matrix of dimension :math:`n`): ``eye(n)``
  - :math:`\text{diag}(\boldsymbol{x})` (diagonal matrix, :math:`\boldsymbol{x}` is a vector): ``diagm(x)``

Matrix operations
------------------------

- :math:`\boldsymbol{A}^T` (transpose): ``A'``
- matrix addition and subtraction: ``+``, ``-``
- matrix-scalar operations ``+``, ``-``, ``*``, ``/`` apply elementwise: ``10 * [1 2; 3 4]`` gives ``[10 20; 30 40]``
- matrix-vector multiplication ``*``. For example, ``[1 2; 3 4]*[5, 6]``:

  .. math::

      \left(
      \begin{array}{cc}
      1 & 2\\
      3 & 4\\
      \end{array}
      \right)
      \left(
      \begin{array}{c}
      5\\
      6\\
      \end{array}
      \right)

- ``*`` is also used for matrix-matrix multiplication

Useful functions
-------------------

- sum of all entries of a matrix: ``sum(A)``
- average of entries of a matrix: ``mean(A)``
- Element-wise *max* and *min*: ``max(A, B)``, ``min(A, B)`` (the arguments must have the same size unless one is a scalar)
- ``norm(A[:])`` or ``vecnorm(A)`` (Note that ``norm(A)`` has a different meaning) means :math:`\left(\sum_{i,j} A_{i,j}^2\right)^{1/2}`

Tricks
==========

Initialization
----------------

Data types
^^^^^^^^^^^^

List (1D **Array**) and matrix (2D or higher dimensional **Array**) may include entries of different types: ``[1, "2", sin, 3.0]``, ``[1, "2"; sin, 3.0]``

.. code:: jlcon

    julia> [1, "2", sin, 3.0]
    4-element Array{Any,1}:
     1
     "2"
     sin
     3.0

    julia> [1 "2"; sin 3.0]
    2x2 Array{Any,2}:
     1      "2"
     sin    3.0

如果元素类型只有常用的数学类型的时候，会按 ``Int64``, ``Rational{Int64}``, ``Float64`` 的顺序进行自动的promotion.
如果元素中有复数，则其余实数类型也会被自动转换为复数，实部和复部类型按之前的顺序自动promotion.

例子如下：

.. code:: jlcon

   julia> [2, 3//4]
   2-element Array{Rational{Int64},1}:
    2//1
    3//4

   julia> [2, 3//4, 0.1]
   3-element Array{Float64,1}:
    2.0
    0.75
    0.1

   julia> [2, 3//4, 0.1, 1+2im]
   4-element Array{Complex{Float64},1}:
     2.0+0.0im
     0.75+0.0im
     0.1+0.0im
     1.0+2.0im

然而，list 或 matrix 的类型也可以进行明确指定。如：

.. code:: jlcon

    julia> Float64[1,2,3]
    3-element Array{Float64,1}:
     1.0
     2.0
     3.0

Empty array
^^^^^^^^^^^^^^

Initialize an empty array. List example (1D array):

.. code:: jlcon

    julia> Float64[]
    0-element Array{Float64,1}

    julia> Array(Float64,0)
    0-element Array{Float64,1}

    julia> Array{Float64}(0)
    0-element Array{Float64,1}

    julia> []
    0-element Array{Any,1}

Matrix example (2D or higher dimensional array), 初始化某一维度为0:

.. code:: jlcon

    julia> Array(Float64,0,2)
    0x2 Array{Float64,2}

    julia> Array{Float64}(0,2)
    0x2 Array{Float64,2}

也可以用 ``reshape`` 函数实现同样效果：

.. code:: jlcon

    julia> reshape([],0,2)
    0x2 Array{Any,2}

Allocate array (no initialization)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Allocate a list (1D array), and fill it with random values. 注：如果数据类型为 Any, 则会被填充未知量。

.. code:: jlcon

    julia> Array(Float64,3)
    3-element Array{Float64,1}:
     1.08099e-314
     1.08097e-314
     1.08098e-314

    julia> Array{Float64}(3)
    3-element Array{Float64,1}:
     0.0
     1.061e-314
     0.0

    julia> Array{Any}(3)
    3-element Array{Any,1}:
     #undef
     #undef
     #undef

上面最后一个式子当然也等同于 ``Array(Any,3)``.

同理，我们也可以创建一个 2x3 矩阵（元素为随机产生）： ``Array(Float64,2,3)`` or ``Array{Float64}(2,3)``

为方便起见，一维和二维的情况下，Julia提供了两个函数, ``Vector(3)``, ``Matrix(2,3)`` 分别相当于 ``Array(Any,3)`` 以及 ``Array(Any,2,3)``.

Initialize a matrix
^^^^^^^^^^^^^^^^^^^^^

创建一个 2x3 矩阵并赋值，可以用下列方式：

1. 按行创建

   .. code:: jlcon

      julia> [1 2 3; 4 5 6]
      2x3 Array{Int64,2}:
       1  2  3
       4  5  6

#. 按列创建

   .. code:: jlcon

      julia> [[1, 4] [2, 5] [3, 6]]
      2x3 Array{Int64,2}:
       1  2  3
       4  5  6

#. 由另一个 list 或 matrix 变形而来

   .. code:: jlcon

      julia> reshape([1,4,2,5,3,6], 2, 3)
      2x3 Array{Int64,2}:
       1  2  3
       4  5  6

.. note:: Julia 是 **列主序**

   * Column-major order: Julia, Fortran, R, Matlab, GNU Octave, BLAS, LAPACK, OpenGL/OpenGL ES
   * ROW-major order: C/C++, Mathematica, Pascal, Python, C#/CLI/.Net, Direct3D

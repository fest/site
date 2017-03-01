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
- ``true``, ``false``, ``==``, ``!=``, ``<``, ``>``, ``<=``, ``>==``, ``!(value == 4)``, ...
- ``exp``, ``sin``, ``pi``, ...
- ``println(23)``, ``quit()``, ``help(sin)``, ``rand()``, ...

Ranges
--------

- ``1:5``, ``0.0:0.1:10.0``, ``linspace(0.0,10.0,11)``
- convert **Range** to **Array**: ``collect(1:5)``

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

Matrices are 2D arrays.

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

To be continued ...

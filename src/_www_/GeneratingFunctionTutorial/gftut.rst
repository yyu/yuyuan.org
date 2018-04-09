
.. raw:: html

	<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>
	<!-- <script type="text/javascript" src="http://localhost:8000/media/mathjax/MathJax.js?config=default"></script> -->
	<link rel="stylesheet" href="math.css" type="text/css">

Generating Fucntion Tutorial
============================

Let's begin with a very famous sequence: :mil:`0\ 1\ 1\ 2\ 3\ 5\ 8\ 13\ 21\ 34\ 55\ 89\ 144` .
They are *Fibonacci numbers*, which can be defined as:

.. math::
	:number: 1
	:label: fibo

	\def\phihat{\rlap{\phi}{\phantom{\hspace{0.4ex}}\widehat{\phantom{\varphi}}}}
	\def\phihats{\rlap{\phi}{\phantom{\hspace{0.1ex}}\widehat{\phantom{\varphi}}}}
	\def\phia{\phi}
	\def\phib{\varphi}
	\def\phic{\phib}
	F_{n}=\begin{cases}
	0 & n=0\\
	1 & n=1\\
	F_{n-1}+F_{n-2} & n>1
	\end{cases}

This is a recursive definition, which is good, but it's not straightforward enough.
For example, if we want to know :mil:`F_{100}`\ , we'll have to calculate
:mil:`F_{0}`, :mil:`F_{1}`, :mil:`\ldots`, :mil:`F_{98}` and :mil:`F_{99}`.
This is a lot of math to do. Is there any better solution? Or, is there a *closed form* for Fibonacci numbers?

Fortunately the answer is *yes*, and (unsurprisingly) *generating function* is such a tool to solve such kinda recurrence.

Generating function is smart and subtle. The only way to understand it is to see how it works by an example.
Here in this tutorial, I'll show you how generating function solves Fibonacci numbers recurrence.

Generally speaking, four steps are needed to solve a recurrence via generating function:

1. Write down a single equation that expresses :mil:`g_{n}` in terms of other elements of the sequence
   (assuming that :mil:`g_{-1}=g_{-2}=\cdots=0`).
2. Multiply both sides of the equation by :mil:`z^{n}` and sum over all :mil:`n`. This gives,
   on the left, the sum :mil:`G(z)=\sum_{n}g_{n}z^{n}`, which is the generating function :mil:`G(z)`.
   The right-hand side should be manipulated so that it becomes some other expression involving :mil:`G(z)`.
3. Solve the resulting equation, getting a closed form for :mil:`G(z)`.
4. Expand :mil:`G(z)` into a power series and read off the coefficient of :mil:`z^n`; this is a closed form for :mil:`g_n`.

Let's apply these steps to Fibonacci numbers.

Step 1
------

At the beginning of this tutorial, we have seen the recursive definition of Fibonacci numbers (equation :eq:`fibo`), but it is not *a single equation*.
So let's simplify it:

.. math::
	:number: 2
	:label: single

	g_{n}=g_{n-1}+g_{n-2}+[n=1]

Note that:

1. We use :mil:`g_{n}` instead of :mil:`F_{n}`.
2. :mil:`[n=1]` is the trick to make *a single equation*, it is defined as :mil:`[n=m] = \begin{cases} 1 & n=m\\ 0 & n\neq m \end{cases}\:`,
   therefore :mil:`[n=1]` equals :mil:`1` iff :mil:`n=1`, which makes :eq:`single` hold for any :mil:`n\ge 0`.

Step 2
------

Let's multiply both sides of equation :eq:`single` by :mil:`z^{n}`:

.. math::
	g_{n}z^{n} = g_{n-1}z^{n} + g_{n-2}z^{n} + [n=1]z^{n}

and sum over all :mil:`n`:

.. math::
	G(z) = \sum_{n}g_{n}z^{n} &= \sum_{n}g_{n-1}z^{n} + \sum_{n}g_{n-2}z^{n} + \sum_{n}[n=1]z^{n} \\
	                          &= n\sum_{n}g_{n-1}z^{n-1} + n^2\sum_{n}g_{n-2}z^{n-2} + z \\
	                          &= n\sum_{n}g_{n}z^{n} + n^2\sum_{n}g_{n}z^{n} + z \\
	                          &= zG(z)+z^{2}G(z)+z

Please keep in your mind that :mil:`G(z)=\sum_{n}g_{n}z^{n}=g_0+g_1z+g_2z^2+\cdots`, that is to say,
if we denote :mil:`G(z)` as a power series, then the coefficients of :mil:`z^n` will be :mil:`F_n`.

Step 3
------

Solve the equation :mil:`G(z)=zG(z)+z^{2}G(z)+z`, getting a closed form for :mil:`G(z)`:

.. math::

	G(z)=\frac{z}{1-z-z^{2}}

Step 4
------

Here comes the hardest part: to expand :mil:`G(z)` into a power series.
How can we do this? Well, there are more than one way to achieve it, but as to this Fibonacci question, there is a simple but smart way.

You may recall that

.. math::
	:number: 3
	:label: alpha

	\frac{1}{1-\alpha z}=1+\alpha z+\alpha^2 z^2+\alpha^3 z^3+\cdots

Similarly we have

.. math::
	:number: 4
	:label: beta

	\frac{1}{1-\beta z}=1+\beta z+\beta^2 z^2+\beta^3 z^3+\cdots

If we add :eq:`alpha` :mil:`\times A` and :eq:`beta` :mil:`\times B`, the left is

.. math::

	\frac{A}{1-\alpha z}+\frac{B}{1-\beta z}=\frac{A+B+(-A\beta-B\alpha)z}{1-(\alpha+\beta)z+\alpha\beta z^2}

and the right is

.. math::

	(A+B) + (A\alpha+B\beta)z + (A\alpha^2+B\beta^2)z^2 + \cdots

Then we realize that if we find the solutions to these two equations:

.. math::
	:number: 5
	:label: two

	      z &= A+B+(-A\beta-B\alpha)z \\
	1-z-z^2 &= 1-(\alpha+\beta)z+\alpha\beta z^2

then

.. math::
	G(z) = \frac{z}{1-z-z^2} &= \frac{A+B+(-A\beta-B\alpha)z}{1-(\alpha+\beta)z+\alpha\beta z^2} \\
	                         &= \frac{A}{1-\alpha z}+\frac{B}{1-\beta z} \\
	                         &= (A+B) + (A\alpha+B\beta)z + (A\alpha^2+B\beta^2)z^2 + \cdots

obviously :mil:`g_n=A\alpha^n+B\beta^n` and we'll be done.

Now all we have to do is to solve :eq:`two`. Fortunately it's no hard job, first we realize that:

.. math::

	A+B             &= 0 \\
	-A\beta-B\alpha &= 1 \\
	\alpha+\beta    &= 1 \\
	\alpha\beta     &= -1

therefore

.. math::

	\alpha &= \frac{1\pm\sqrt{5}}{2} \\
	\beta  &= \frac{1\mp\sqrt{5}}{2} \\
	A      &= \pm\frac{1}{\sqrt{5}} \\
	B      &= \mp\frac{1}{\sqrt{5}}

.. different phi
   Φφϕᵠᵩ𝚽𝛗𝛟𝛷𝜑𝜙𝜱𝝋𝝓𝝫𝞅𝞍𝞥𝞿𝟇
   \phia\phib\phic
   \widehat{\phia}\hat{\phia}
   \widehat{ϕ}\hat{ϕ}

in which

- :mil:`\alpha` and :mil:`\beta` are symmetric, so do :mil:`A` and :mil:`B`, so we can use :mil:`+` and :mil:`-` instead of :mil:`\pm` and :mil:`\mp`.
- :mil:`\frac{1+\sqrt{5}}{2}` is the *golden ratio*. In this article let's denote it as :mil:`\phia`.
  :mil:`\frac{1-\sqrt{5}}{2}` will be denoted as :mil:`\phib`.

Therefore

.. math::

	\alpha &= \phia \\
	\beta  &= \phib \\
	A      &=  \frac{1}{\sqrt{5}} \\
	B      &= -\frac{1}{\sqrt{5}}


We can expand :mil:`G(z)` now:

.. math::

	G(z) &= \frac{z}{1-z-z^{2}} \\
	     &= (A+B) + (A\alpha+B\beta)z + (A\alpha^2+B\beta^2)z^2 + \cdots \\
	     &= 0 + \frac{\phia-\phib}{\sqrt{5}}z + \frac{\phia^2-\phib^2}{\sqrt{5}}z^2 + \cdots

We can read off the coefficient of :mil:`z^n`:

.. math::

	g_n=\frac{\phia^{n}-\phib^{n}}{\sqrt{5}}

In other words, the :mil:`n`\ th Fibonacci number is :mil:`\frac{\phia^{n}-\phic^{n}}{\sqrt{5}}`.

Summary
-------

This is amazing.
We introduce :mil:`z^n`, then we use :mil:`z^n` and the unknown :mil:`g_n` (here :mil:`g_n` is :mil:`F_n`) to construct a :mil:`G(z)`,
finally we expand :mil:`G(z)` to get :mil:`g_n`.
It's like music: we have a subject, then we develop it and eventually we come back to it.

Please note that :mil:`z` and :mil:`G(z)` are meaningful only because we care about the coefficients of :mil:`z^n`.
We don't care what :mil:`z` is, neither do we care what :mil:`G(z)` is.
What we care is the expanded form of :mil:`G(z)`, so once we have a :mil:`G(z)`, we focus on how to expand it.

Generating function is beautiful and very powerful. You must have seen this in this tutorial.
If you want to learn more, I suggest you read [GKP]_.
This tutorial is actually a note I made when I read the book.
Fibonacci numbers are amazing. If you read [GKP]_, you'll find more discussions in Chapter 6 and Chapter 7.

.. [GKP] Ronald L. Graham, Donald E. Knuth, and Oren Patashnik, Concrete Mathematics: A Foundation for Computer Science. Addison-Wesley, 1989; second edition, 1994.


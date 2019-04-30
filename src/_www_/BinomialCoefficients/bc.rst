.. raw:: html

        <!-- <script type="text/javascript" src="https://localhost:8000/media/mathjax/MathJax.js?config=default"></script> -->
        <script type="text/javascript" src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
        <link rel="stylesheet" href="math.css" type="text/css">

Interesting Binomial Coefficients
=================================

.. math::
	\binom{n}{k} = \frac{n(n-1)\ldots(n-k+1)}{k(k-1)\ldots(1)}

Binomial coefficients have a lot of interesting properties.
The following are some of them.

- Each is shown with both a mathematical formula and an illustration.
- Each illustration reveals some relationship between numbers in the Pascal's triangle, which can be considered as the *meaning* of the formula.

Most of the formulas are important. Some of them are very important. They deserve our careful studies.

1. :mil:`\binom{n}{k} = \binom{n}{n-k}`

   .. image:: a.jpg
      :width: 400
      :align: center

   .. math::
      \binom{n}{k} &= \binom{n}{n-k},\qquad {\rm integer}\; n\ge 0,\; {\rm integer}\; k. \\
      \binom{5}{1} &= \binom{5}{5-1}

2. :mil:`\binom{r}{k}=\frac{r}{k}\binom{r-1}{k-1}`

   .. image:: b.jpg
      :width: 400
      :align: center

   .. math::
      \binom{r}{k} &= \frac{r}{k}\binom{r-1}{k-1},\qquad {\rm integer}\; k\neq 0. \\
      \binom{7}{2} &= \frac{7}{2}\binom{7-1}{2-1}

3. :mil:`\binom{r}{k} = \frac{r}{r-k}\binom{r-1}{k}`

   .. image:: c.jpg
      :width: 400
      :align: center

   .. math::
      \binom{r}{k} &= \frac{r}{r-k}\binom{r-1}{k},\qquad {\rm integer}\; k\neq r. \\
      \binom{7}{3} &= \frac{7}{7-3}\binom{7-1}{3}

4. :mil:`\binom{r}{k} = \binom{r-1}{k} + \binom{r-1}{k-1}`

   .. image:: d.jpg
      :width: 400
      :align: center

   .. math::
      \binom{r}{k} &= \binom{r-1}{k} + \binom{r-1}{k-1},\qquad {\rm integer}\; k. \\
      \binom{7}{3} &= \binom{6}{3} + \binom{6}{2}

5. :mil:`\sum_{0\leq k\leq n}\binom{r+k}{k}=\binom{r}{0}+\binom{r+1}{1}+\cdots+\binom{r+n}{n}=\binom{r+n+1}{n}`

   .. image:: e.jpg
      :width: 400
      :align: center

   .. math::
      \sum_{0\leq k\leq n}\binom{r+k}{k} &= \binom{r}{0}+\binom{r+1}{1}+\cdots+\binom{r+n}{n}=\binom{r+n+1}{n},\qquad{\rm integer}\; n\geq0. \\
      \sum_{0\leq k\leq 3}\binom{4+k}{k} &= \binom{4}{0}+\binom{4+1}{1}+\cdots+\binom{4+3}{3}=\binom{4+3+1}{3}

6. :mil:`\sum_{0\leq k\leq n}\binom{k}{m}=\binom{0}{m}+\binom{1}{m}+\cdots+\binom{n}{m}=\binom{n+1}{m+1}`

   .. image:: f.jpg
      :width: 400
      :align: center

   .. math::
      \sum_{0\leq k\leq n}\binom{k}{m} &= \binom{0}{m}+\binom{1}{m}+\cdots+\binom{n}{m}=\binom{n+1}{m+1},\qquad{\rm integer}\; m\geq0,\;{\rm integer}\; n\geq0. \\
      \sum_{0\leq k\leq 7}\binom{k}{2} &= \binom{0}{2}+\binom{1}{2}+\cdots+\binom{7}{2}=\binom{7+1}{2+1}

7. :mil:`\binom{-r}{k}=(-1)^{k}\binom{r+k-1}{k}`

   .. image:: g.jpg
      :width: 400
      :align: center

   .. math::
      \binom{-r}{k} &= (-1)^{k}\binom{r+k-1}{k},\qquad{\rm integer}\; k. \\
      \binom{-3}{5} &= (-1)^{5}\binom{3+5-1}{5}

8. :mil:`\sum_{k\leq n}\binom{r}{k}(-1)^{k}=\binom{r}{0}-\binom{r}{1}+\cdots+(-1)^{n}\binom{r}{n}=(-1)^{n}\binom{r-1}{n}`

   .. image:: h.jpg
      :width: 400
      :align: center

   .. math::
      \sum_{k\leq n}\binom{r}{k}(-1)^{k} &= \binom{r}{0}-\binom{r}{1}+\cdots+(-1)^{n}\binom{r}{n}=(-1)^{n}\binom{r-1}{n},\qquad{\rm integer}\; n\geq0. \\
      \sum_{k\leq 3}\binom{7}{k}(-1)^{k} &= \binom{7}{0}-\binom{7}{1}+\cdots+(-1)^{3}\binom{7}{3}=(-1)^{3}\binom{7-1}{3}

9. :mil:`\binom{n}{m}=(-1)^{n-m}\binom{-(m+1)}{n-m}`

   .. image:: i.jpg
      :width: 400
      :align: center

   .. math::
      \binom{n}{m} &= (-1)^{n-m}\binom{-(m+1)}{n-m},\qquad{\rm integer}\; n\geq0,\;{\rm integer}\; m. \\
      \binom{n}{3} &= (-1)^{n-3}\binom{-(3+1)}{n-3}

**References**:

- Ronald L. Graham, Donald E. Knuth, and Oren Patashnik, Concrete Mathematics: A Foundation for Computer Science. Addison-Wesley, 1989; second edition, 1994.
- Donald E. Knuth, The Art of Computer Programming, volume 1: Fundamental Algorithms. Addison-Wesley, 1968; third edition, 1997.


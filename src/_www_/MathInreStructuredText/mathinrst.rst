.. comments
    .. sidebar:: Contents

.. raw:: html

   <script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS_HTML"> </script>
   <link rel="stylesheet" href="math.css" type="text/css">

Math in reStructuredText
========================

.. contents:: Table of Contents

Math in Browser
---------------

There are many ways to embed math formulas into a web page.

Solution 1: MathML
``````````````````

MathML is a W3C Recommendation [#W3Cmath]_, so you might guess it is the best choice, but it is not,
because it is not supported well by the major web browsers [#MMLsupport]_ (see [#MMLtest]_).

If you want to use MathML, you still have a decision to make: do you want to write the MathML code by yourself?

If you decide to write your formulas in MathML directly, it's OK. However, you don't have to write it if you don't want to.
Instead, you can write in :mil:`\rm \LaTeX` and convert it into MathML using tools such as itex2MML [#itex2MML]_.

.. [#W3Cmath] http://www.w3.org/Math/
.. [#MMLsupport] http://en.wikipedia.org/wiki/MathML#Web_browsers
.. [#MMLtest] http://www.w3.org/Math/testsuite/
.. [#itex2MML] http://golem.ph.utexas.edu/~distler/blog/itex2MML.html

Solution 2: JavaScript + CSS
````````````````````````````

The fact that HTML is not :mil:`\rm \LaTeX`-friendly does not mean that web browsers are not :mil:`\rm \LaTeX`-friendly,
because browsers are powered by JavaScript and CSS.
JavaScript can parse :mil:`\rm \LaTeX` codes and render them with the help of CSS, which can display really fancy math in a browser.
MathJax [#mathjax]_ is such a tool.
All you have to do is to insert a line in your HTML::

	<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS_HTML"> </script>

Then you can write Math in :mil:`\rm \LaTeX` now::

	\[ \frac{1}{\Bigl(\sqrt{\phi \sqrt{5}}-\phi\Bigr) e^{\frac25 \pi}} =
	1+\frac{e^{-2\pi}} {1+\frac{e^{-4\pi}} {1+\frac{e^{-6\pi}}
	{1+\frac{e^{-8\pi}} {1+\ldots} } } } \]

This will be rendered as

.. math::

	\frac{1}{\Bigl(\sqrt{\phi \sqrt{5}}-\phi\Bigr) e^{\frac25 \pi}} =
	1+\frac{e^{-2\pi}} {1+\frac{e^{-4\pi}} {1+\frac{e^{-6\pi}}
	{1+\frac{e^{-8\pi}} {1+\ldots} } } }

More demos can be found on the official MathJax website [#mathjaxsamples]_.

Please note that MathJax can convert :mil:`\rm \LaTeX` into MathML too, so choosing MathJax means you get the flexibility to switch between CSS and MathML.

In fact MathJax is not the only JS+CSS solution. There are other similar tools, such as jsMath [#jsMath]_ [#wikijsMath]_ and jqMath [#jqMath]_.

jsMath seems the predecessor of MathJax (from Wikipedia [#wikiMathJax]_):

	The MathJax project started in 2009 as the successor to an earlier JavaScript mathematics formatting library, jsMath, and
	is managed by Design Science. The project is sponsored by the American Mathematical Society, Design Science, and the Society
	for Industrial and Applied Mathematics and is supported by the American Physical Society, Elsevier, and Project Euclid.

	MathJax is used by web sites including MathSciNet, GitHub, n-category cafe, Math Overflow, Project Euclid journals, and the
	All-Russian Mathematical Portal.

.. [#mathjax] http://www.mathjax.org
.. [#mathjaxsamples] http://www.mathjax.org/demos/tex-samples/
.. [#jsMath] http://www.math.union.edu/~dpvc/jsmath/
.. [#wikijsMath] http://en.wikipedia.org/wiki/JsMath
.. [#jqMath] http://mathscribe.com/author/jqmath.html
.. [#wikiMathJax] http://en.wikipedia.org/wiki/Mathjax

Solution 3: Image
`````````````````

Almost all browsers support images, so if you don't trust anything (like MathML, MathJax, etc.), use images.

There are many tools that can convert :mil:`\rm \LaTeX` into images, such as
Mathhack [#Mathhack]_,
LatexFormulaMacro [#LatexFormulaMacro]_,
django_mathlatex [#django_mathlatex]_ (if you use Django),
etc.

.. [#Mathhack] http://docutils.sourceforge.net/sandbox/cben/rolehack/
.. [#LatexFormulaMacro] http://trac-hacks.org/wiki/LatexFormulaMacro
.. [#django_mathlatex] https://github.com/emesik/django_mathlatex

Comparison of solutions
```````````````````````

================  ===================  ==========================  ==================================  ===========================================
option            web browser support  look the same in browsers?  usage                               users
================  ===================  ==========================  ==================================  ===========================================
MathML            poor                 no                          embed MathML into HTML              currently no website really uses it
----------------  -------------------  --------------------------  ----------------------------------  -------------------------------------------
Image             perfect              yes                         make images and embed them in HTML  - Wikipedia
----------------  -------------------  --------------------------  ----------------------------------  -------------------------------------------
MathJax (JS+CSS)  very good            almost yes                  embed :mil:`\rm \LaTeX` in HTML     - StackExchange [#stackexchange]_
                                                                                                       - CERN document server [#cern]_, [#cern1]_
                                                                                                       - The Annals of Mathematics [#princeton]_
                                                                                                       - etc. [#mathjaxinuse]_
================  ===================  ==========================  ==================================  ===========================================

.. [#stackexchange] http://math.stackexchange.com/
.. [#cern] http://cdsweb.cern.ch/
.. [#cern1] http://cdsweb.cern.ch/record/1330928
.. [#princeton] http://annals.math.princeton.edu/
.. [#mathjaxinuse] http://www.mathjax.org/community/mathjax-in-use/

My Choice
`````````

So far MathML is obviously not a good choice.
Between JS+CSS and image, I choose the former, because I want the formulas to be rendered at runtime.
If I use image, I would have to convert the math into images, store it in some place and embed them in HTML, which would be less convenient.

MathJax and jsMath are very similar.
Both MathJax and jsMath are used by many websites [#jsmathinuse]_, but
I prefer MathJax because it's newer and is supported by many famous commercial and academic sites such as
[#stackexchange]_, [#cern]_, [#princeton]_.

jqMath is another option. It is said that it is much faster than MathJax [#jqmath-mathjax]_, but I didn't try it.
It seems fewer sites are using it. Maybe I should give it a try later.

.. [#jsmathinuse] http://www.math.union.edu/~dpvc/jsmath/gallery.html
.. [#jqmath-mathjax] http://mathscribe.com/author/jqmath-mathjax-perf.html

Use MathJax in reStructuredText
-------------------------------

No hacking is needed to use MathJax in reStructuredText. We can just use the ``raw`` directive::
		
	math.rst::
		
		.. role:: raw-latex(raw)
		    :format: latex html

		.. raw:: html

		   <script type="text/javascript" src="http://localhost/mathjax/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>

		This: :raw-latex:`\((x+a)^3\)`

		this: :raw-latex:`\(W \approx \sum{f(x_k) \Delta x}\)`

		this: :raw-latex:`\(W = \int_{a}^{b}{f(x) dx}\)`

		and this:

		.. raw:: latex html

		   \[ \frac{1}{\Bigl(\sqrt{\phi \sqrt{5}}-\phi\Bigr) e^{\frac25 \pi}} =
		   1+\frac{e^{-2\pi}} {1+\frac{e^{-4\pi}} {1+\frac{e^{-6\pi}}
		   {1+\frac{e^{-8\pi}} {1+\ldots} } } } \]

		When :raw-latex:`\(a \ne 0\)`, there are two solutions to :raw-latex:`\(ax^2 + bx + c = 0\)` and they are
		:raw-latex:`\(x = {-b \pm \sqrt{b^2-4ac} \over 2a}.\)`

You will get this:

	This: :mil:`(x+a)^3`

	this: :mil:`W \approx \sum{f(x_k) \Delta x}`

	this: :mil:`W = \int_{a}^{b}{f(x) dx}`

	and this:

	.. math::

	    \frac{1}{\Bigl(\sqrt{\phi \sqrt{5}}-\phi\Bigr) e^{\frac25 \pi}} =
	    1+\frac{e^{-2\pi}} {1+\frac{e^{-4\pi}} {1+\frac{e^{-6\pi}}
	    {1+\frac{e^{-8\pi}} {1+\ldots} } } }

	When :mil:`a \ne 0`, there are two solutions to :mil:`ax^2 + bx + c = 0` and they are :mil:`x = {-b \pm \sqrt{b^2-4ac} \over 2a}.`

Use MathJax in a Django project
-------------------------------

I mentioned in `my home page <http://forrestyu.net/>`_ that all articles in this site are stored as reStructuredText format.
`Some of the articles <http://forrestyu.net/art/generating-fucntion-tutorial/>`_ contains math formula.
Here's what I did in my Django project.

Use a custom module for our custom stuff
````````````````````````````````````````

We will use some custom stuff, so let's create a custom module::

	$ mkdir rsthack
	$ cd rsthack
	$ touch __init__.py
	$ ln -s /path/to/rsthack /path/to/a/module/search/path/

The code for new roles and new directive will be put in the __init__.py.

Add a new role ``mil``
``````````````````````

``mil`` stands for **m**\ *ath* **i**\ *n*\ **l**\ *ine*.

	.. colorcode:: python

		class_name = 'mathjaxlatex'  # appears in <span class="mathjaxlatex"> and <div class="mathjaxlatex">

		def MRole(role, rawtext, text, lineno, inliner, options={}, content=[]):
		    t = re.sub(':%s:' % role, '', rawtext)
		    assert t[:1] == '`' and t[-1:] == '`'
		    t = r'\(%s\)' % t[1:-1]
		    options={'format': 'html', 'classes': [class_name]}
		    node = nodes.raw(rawtext, t, **options)
		    return [node], []

		roles.register_canonical_role('mil', MRole)

Then we can use ``:mil:`x = {-b \pm \sqrt{b^2-4ac} \over 2a}``` to get :mil:`x = {-b \pm \sqrt{b^2-4ac} \over 2a}`.

Add new directive ``math`` and new role ``eq``
``````````````````````````````````````````````

The code for role ``eq`` is simple, but the code for directive ``math`` is a little more complicated.
Most lines below are cloned from `Sphinx <http://sphinx.pocoo.org/>`_ source.

	.. colorcode:: python

		######################################################################
		# role eq
		######################################################################
		# see: /usr/share/pyshared/sphinx/ext/mathbase.py

		class eqref(nodes.Inline, nodes.TextElement):
		    pass

		def html_visit_eqref(self, node):
		    self.body.append('<a href="#equation-%s">' % node['target'])

		def html_depart_eqref(self, node):
		    self.body.append('</a>')

		def eq_role(role, rawtext, text, lineno, inliner, options={}, content=[]):
		    text = utils.unescape(text)
		    node = eqref('(?)', '(?)', target=text)
		    return [node], []

		roles.register_canonical_role('eq', eq_role)

		######################################################################
		# directive math
		######################################################################
		# see:
		#     /usr/share/pyshared/sphinx/application.py
		#     /usr/share/pyshared/sphinx/ext/mathbase.py
		#     /usr/share/pyshared/sphinx/ext/jsmath.py
		#     /usr/share/doc/python-sphinx/html/ext/math.html

		def massage_equations(doctree):
		    num = 0
		    numbers = {}

		    # generate the "label->number" map from directive ``math``
		    for node in doctree.traverse(displaymath):
			if node['number'] is None:
			    continue
			numbers[node['label']] = node['number']

		    # set eqno in references
		    for node in doctree.traverse(eqref):
			if node['target'] not in numbers:
			    continue
			num = '(%d)' % numbers[node['target']]
			node[0] = nodes.Text(num, num)

		def html_visit_displaymath(self, node):
		    if node['nowrap']:
			self.body.append(self.starttag(node, 'div', CLASS=class_name))
			self.body.append(node['latex'])
			self.body.append('</div>')
			raise nodes.SkipNode
		    for i, part in enumerate(node['latex'].split('\n\n')):
			part = self.encode(part)
			if i == 0:
			    # necessary to e.g. set the id property correctly
			    if node['number'] is not None:
				self.body.append('<span class="eqno">(%s)</span>' %
						 node['number'])
			    self.body.append(self.starttag(node, 'div', CLASS=class_name))
			else:
			    # but only once!
			    self.body.append('<div class="%s">' % class_name)
			if '&' in part or '\\\\' in part:
			    self.body.append('\\[\\begin{align}\n' + part + '\n\\end{align}\\]')
			else:
			    self.body.append('\\[' + part + '\\]')
			self.body.append('</div>\n')
		    raise nodes.SkipNode

		def add_node(node, **kwds):
		    nodes._add_node_class_names([node.__name__])
		    for key, val in kwds.iteritems():
			try:
			    visit, depart = val
			except ValueError:
			    raise ExtensionError('Value for key %r must be a '
						 '(visit, depart) function tuple' % key)

			assert key == 'html', 'accept html only'

			setattr(translator, 'visit_'+node.__name__, visit)
			if depart:
			    setattr(translator, 'depart_'+node.__name__, depart)

		class displaymath(nodes.Part, nodes.Element):
		    pass

		# custom directive ``math``
		class MathDisplay(Directive):
		    has_content = True
		    required_arguments = 0
		    optional_arguments = 1
		    final_argument_whitespace = True
		    option_spec = {
			'label':  directives.unchanged,
			'nowrap': directives.flag,
			'number': directives.nonnegative_int,
		    }

		    def run(self):
			latex = '\n'.join(self.content)
			if self.arguments and self.arguments[0]:
			    latex = self.arguments[0] + '\n\n' + latex
			node = displaymath()
			node['latex']  = latex
			node['number'] = self.options.get('number', None)
			node['label']  = self.options.get('label', node['number'])
			node['nowrap'] = 'nowrap' in self.options

			ret = [node]

			if node['label']:
			    tnode = nodes.target('', '', ids=['equation-' + node['label']])
			    self.state.document.note_explicit_target(tnode)
			    ret.insert(0, tnode)
			return ret

		add_node(eqref, html=(html_visit_eqref, html_depart_eqref))
		add_node(displaymath, html=(html_visit_displaymath, None))

		directives.register_directive('math', MathDisplay)

		
Write a custom Django filter
````````````````````````````

The code above are in our custom module ``rsthack``, so everytime we ``import rsthack``,
the code will run and we are ready to use the new roles, new directive and stuff.

One trick in the following filter is that we call ``rsthack.massage_equations`` to set the correct equation numbers in references.
		
	.. colorcode:: python

		##############################
		# filter enhancedrst
		##############################

		from django.conf import settings
		from django.utils.encoding import smart_str, force_unicode
		from django.utils.safestring import mark_safe
		
		import rsthack  # run rsthack/__init__.py

		def enhancedrst(value):
		    try:
			from docutils import io
			from docutils.core import publish_doctree, Publisher
			from docutils.readers.doctree import Reader
		    except ImportError:
			if settings.DEBUG:
			    raise template.TemplateSyntaxError("Error in {% restructuredtext %} filter: The Python docutils library isn't installed.")
			return force_unicode(value)
		    else:
			docutils_settings = getattr(settings, "RESTRUCTUREDTEXT_FILTER_SETTINGS", {})

			# generate the doctree
			document = publish_doctree(source=smart_str(value), source_class=io.StringInput)

			# connect eqno and the reference
			rsthack.massage_equations(document)

			# apply the massaged doctree
			# (this is almost the same as docutils.core.publish_from_doctree)
			pub = Publisher(Reader(parser_name='null'),
					None, None,
					source=io.DocTreeInput(document),
					destination_class=io.StringOutput)
			pub.set_writer('html4css1')
			pub.process_programmatic_settings(None, docutils_settings, None)
			pub.set_destination(None, None)
			pub.publish()
			parts = pub.writer.parts

			return mark_safe(force_unicode(parts["fragment"]))

		enhancedrst.is_safe = True

		register.filter(enhancedrst)

Use the new filter
``````````````````

A Django template sample::

    {% load rst %}
    <link rel="stylesheet" type="text/css" href="{{ mediaurl }}css/rst.css" />
    <script type="text/javascript" src="{{ mathjax }}"></script>
    {% for art in articles %}
        <blockquote>
        {{ art.content|enhancedrst }}
        </blockquote>
    {% endfor %}

in which

- the filter source is part of file rst.py, so we use ``load rst`` to load it
- in rst.css we mush have
	.. colorcode:: css

		span.eqno {
			float: right;
		}
- the URL ``mathjax`` can be either the MathJax CDN or your own MathJax URL [#mathjaxloading]_
- ``art.content`` should be in reStructuredText format
		
.. [#mathjaxloading] http://www.mathjax.org/docs/1.1/configuration.html

Write math in Django
````````````````````

Now everything's ready. Let's write math in our article::

	When :mil:`a \ne 0`, there are two solutions to :mil:`ax^2 + bx + c = 0` and they are
	:mil:`x = {-b \pm \sqrt{b^2-4ac} \over 2a}.`

	Some *big* math:
	.. math::
	    :number: 123
	    :label: blah

	    \frac{1}{\Bigl(\sqrt{\phi \sqrt{5}}-\phi\Bigr) e^{\frac25 \pi}} =
	    1+\frac{e^{-2\pi}} {1+\frac{e^{-4\pi}} {1+\frac{e^{-6\pi}}
	    {1+\frac{e^{-8\pi}} {1+\ldots} } } }

	Did you know equation :eq:`blah`?

We will get:

	When :mil:`a \ne 0`, there are two solutions to :mil:`ax^2 + bx + c = 0` and they are
	:mil:`x = {-b \pm \sqrt{b^2-4ac} \over 2a}.`

	Some *big* math:

	.. math::
	    :number: 123
	    :label: blah

	    \frac{1}{\Bigl(\sqrt{\phi \sqrt{5}}-\phi\Bigr) e^{\frac25 \pi}} =
	    1+\frac{e^{-2\pi}} {1+\frac{e^{-4\pi}} {1+\frac{e^{-6\pi}}
	    {1+\frac{e^{-8\pi}} {1+\ldots} } } }

	Did you know equation :eq:`blah`?

Get the code
````````````

Most of the code above is available in `Google Code <http://code.google.com/p/forrest/>`_. You can either
`read online <http://code.google.com/p/forrest/source/browse/src/rsthack/__init__.py>`_
or `check it out <http://code.google.com/p/forrest/source/checkout>`_ from the repository.

Extra readings
--------------

future release of docutils may support :mil:`\rm \LaTeX` math
`````````````````````````````````````````````````````````````

- http://stackoverflow.com/questions/3610551/math-in-restructuredtext-with-latex
- http://article.gmane.org/gmane.text.docutils.user/6255

JSXGraph
````````

- http://jsxgraph.uni-bayreuth.de/wp/
- https://groups.google.com/forum/#!topic/mathjax-users/ER-pN6TSplU

GMailTeX
````````

- http://alexeev.org/gmailtex.html

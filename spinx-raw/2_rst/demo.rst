=====================================
 An Introduction to reStructuredText
=====================================
Author: David Goodger
Contact: dgoodger@bigfoot.com
Status: second draft
Date: 2001-06-02

reStructuredText_ is a proposed revision and reinterpretation of the
StructuredText_ and Setext_ lightweight markup systems. reStructuredText is
useful for quickly creating simple web pages and for in-line program
documentation (in comments of any programming language, or in documentation
strings of languages such as Python and Emacs Lisp). It can be used in
systems which extract in-line comments and docstrings to create API
documentation.

reStructuredText is designed for extensibility for specific application
domains. It is a candidate markup syntax for the `Python Docstring
Processing System`_.

This document defines the goals_ of reStructuredText, provides a history_
of the project, and outlines a `parser implementation plan`_. It is also
written with the reStructuredText markup, therefore serves as an example of
its use. Please also see an analysis of the problems of StructuredText, and
the reStructuredText markup specification itself (general and Python
extensions), all on the project's web site, http://structuredtext.sf.net/.

.. _reStructuredText: http://structuredtext.sf.net
.. _StructuredText:
    http://dev.zope.org/Members/jim/StructuredTextWiki/FrontPage
.. _Setext: http://www.bsdi.com/setext
.. _Python Docstring Processing System: http://docstring.sf.net

.. _goals:

Goals
=====

The primary goal of reStructuredText_ is to define a markup syntax for use
in Python docstrings and other documentation domains, that is readable and
simple, yet powerful enough for non-trivial use. The intended purpose of
the markup is the conversion of reStructuredText documents into useful
structured data formats.

The secondary goal of reStructuredText is to be accepted by the Python
community (by way of being blessed by PythonLabs and the BDFL [1]_) as a
standard for Python inline documentation (possibly one of several
standards, to account for taste).

.. _[1] Python's creator and "Benevolent Dictator For Life",
   Guido van Rossum.

To clarify the primary goal, here are specific design goals, in order,
beginning with the most important:

1. Readable: The marked-up text must be easy to read without any prior
   knowledge of the markup language. It should be as easily read in raw
   form as in processed form.

2. Unobtrusive: The markup that is used should be as simple and unobtrusive
   as possible. The simplicity of markup constructs should be roughly
   proporional to their frequency of use.

3. Unambiguous: The rules for markup must not be open for interpretation.
   For any given input, there should be one and only one possible output
   (including error output).

4. Unsurprising: Markup constructs should not cause unexpected output upon
   processing. As a fallback, there must be a way to prevent unwanted
   markup processing when a markup construct is used in a non-markup
   context (for example, when documenting the markup syntax itself).

5. Intuitive: Markup should be as obvious and easily remembered as
   possible, for the author as well as for the reader. Constructs should
   take their cues from such naturally occurring sources as plaintext email
   messages and newsgroup postings.

6. Easy: It should be easy to mark up text using any ordinary text editor.

7. Scalable: The markup should be applicable regardless of the length of
   the text.

8. Powerful: The markup should provide enough constructs to produce a
   reasonably rich structured document.

9. Language-neutral: The markup should apply to multiple natural (as well
   as artificial) languages, not only English.

10. Extensible: The markup should provide a simple syntax and interface for
    adding more complex general markup, and custom markup.

11. Output-format-neutral: The markup will be appropriate for processing to
    multiple output formats, and will not be biased toward any particular
    format.

The design goals above were used as criteria for accepting or rejecting
syntax, or selecting between alternatives.

It is emphatically *not* the goal of reStructuredText to define docstring
semantics, such as docstring contents or docstring length. These issues are
orthogonal to the markup syntax and beyond the scope of this proposal.

Also, it is not the goal of reStructuredText to maintain compatibility with
StructuredText_ or Setext_. reStructuredText shamelessly steals their great
ideas and ignores the not-so-great.

Author's note:

    Due to the nature of the problem we're trying to solve (or, perhaps,
    due to the nature of the proposed solution), the above goals
    unavoidably conflict. I have tried to extract and distill the wisdom
    accumulated over the years in the Python Doc-SIG_ mailing list and
    elsewhere, to come up with a coherent and consistent set of syntax
    rules, and the above goals by which to measure them.

    There will inevitably be people who disagree with my particular
    choices. Some desire finer control over their markup, others prefer
    less. Some are concerned with very short docstrings, others with
    full-length documents. This specification is an effort to provide a
    reasonably rich set of markup constructs in a reasonably simple form,
    that should satisfy a reasonably large group of reasonable people.

    David Goodger (dgoodger@bigfoot.com), 2001-04-20

.. _Doc-SIG: http://www.python.org/sigs/doc-sig/

.. _history:

History
=======
reStructuredText_, the specification, is based on StructuredText_ and
Setext_. StructuredText was developed by Jim Fulton of `Digital Creations`_
and first released in 1996. It is now released as a part of the open-source
'Z Object Publishing Environment' (ZOPE_). Ian Feldman's and Tony Sanders'
earlier Setext_ specification was either an influence on StructuredText or,
by their similarities, at least evidence of the correctness of this
approach.

I discovered StructuredText_ in late 1999 while searching for a way to
document the Python modules in one of my projects. Version 1.1 of
StructuredText was included in Daniel Larsson's pythondoc_. Although I was
not able to get pythondoc to work for me, I found StructuredText to be
almost ideal for my needs. I joined the Python Doc-SIG_ (Documentation
Special Interest Group) mailing list and found an ongoing discussion of the
shortcomings of the StructuredText 'standard'. This discussion has been
going on since 1996.

I decided to modify the original module with my own extensions and some
suggested by the Doc-SIG members. I soon realized that the module was not
written with extension in mind, so I embarked upon a general reworking,
including adapting it to the 're' regular expression module (the original
inspiration for the name of this project). Soon after I completed the
modifications, I discovered that StructuredText.py was up to version 1.23
in the ZOPE distribution. Implementing the new syntax extensions from
version 1.23 proved to be an exercise in frustration, as the complexity of
the module had become overwhelming.

Recently, development on StructuredTextNG_ ("Next Generation") has begun at
Digital Creations. It seems to have many improvements, but still suffers
from many of the problems of classic StructuredText.

I decided that a complete rewrite was in order, and even started a
SourceForge project, reStructuredText_. My motivations (the 'itches' I aim
to 'scratch') are as follows:

- I need a standard format for inline documentation of the programs I
  write. This inline documentation has to be convertible to other useful
  formats, such as HTML. I believe many others have the same need.

- I believe in the Setext/StructuredText idea and want to help formalize
  the standard. However, I feel the current specifications and
  implementations have flaws that desperately need fixing.

- reStructuredText could form part of the foundation for a documentation
  extraction and processing system, greatly benefitting Python. But it is
  only a part, not the whole. reStructuredText is a markup language
  specification and (soon to be) a reference parser implementation, but it
  does not aspire to be the entire system. I don't want reStructuredText or
  a hypothetical Python documentation processor to die stillborn because of
  overambition.

- Most of all, I want to help ease the documentation chore, the bane of
  many a programmer.

Unfortunately I was sidetracked and stopped working on this project. In
November 2000 I made the time to enumerate the problems of StructuredText
and possible solutions, and complete the first draft of a specification.
This first draft was posted to the Doc-SIG in three parts:

- `A Plan for Structured Text`_
- `Problems With StructuredText`_
- `reStructuredText: Revised Structured Text Specification`_

In March 2001 a flurry of activity on the Doc-SIG spurred me to further
revise and refine my specification, the result of which you are now
reading. An offshoot of the reStructuredText project has been the
realization that a single markup scheme, no matter how well thought out,
was not enough. In order to tame the endless debates on Doc-SIG, a flexible
`Docstring Processing System`_ framework needed to be constructed. This
framework has become the more important of the two projects;
reStructuredText has found its place as one possible choice for a single
component of the larger framework.

.. _Digital Creations: http://www.digicool.com
.. _ZOPE: http://www.zope.org
.. _pythondoc: http://starship.python.net/crew/danilo/pythondoc/
.. _StructuredTextNG:
    http://dev.zope.org/Members/jim/StructuredTextWiki/StructuredTextNG
.. _A Plan for Structured Text:
    http://mail.python.org/pipermail/doc-sig/2000-November/001239.html
.. _Problems With StructuredText:
    http://mail.python.org/pipermail/doc-sig/2000-November/001240.html
.. _[reStructuredText: Revised Structured Text Specification]:
    http://mail.python.org/pipermail/doc-sig/2000-November/001241.html
.. _Docstring Processing System: http://docstring.sf.net

.. _parser implementation plan:

Parser Implementation Plan
==========================
The author will implement a reStructuredText parser in stages, listed
below. It will be posted to the `project web site`_, and contributions (of
testing, bug reports, patches, administration, encouragement, cookies,
large sums of money, etc.) will be welcome. Of course, anyone else is free
to begin their own implementation of this markup syntax or alternatives.

The parser will be implemented in 4 stages, according to the complexity
level and expected frequency of use of the syntax constructs:

1. General markup, level 1

   - escaping mechanism, using backslash

   - body elements

     - paragraphs
     - literal blocks
     - bullet lists

   - inline markup

     - emphasis
     - strong
     - interpreted text
     - inline literals

   - structural markup

     - section headers

   - extension markup

     - directives
     - comments

2. General markup, level 2

   - body elements

     - definition lists
     - block quotes
     - footnotes
     - internal/indirect hyperlink targets

   - inline markup

     - standalone (direct external) hyperlinks
     - indirect external hyperlinks
     - internal hyperlinks
     - footnote references

3. General markup, level 3

   - body elements

     - enumerated lists
     - field lists
     - tables

4. Python-specific markup

   - body elements

     - doctest blocks
     - option lists

   - inline markup

     - interpreted text (Python interpretation thereof)

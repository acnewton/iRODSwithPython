---
title: "Basic data handling with iRODS API"
teaching: 10
exercises: 0
questions:
- "How can you connect to iRODS instance and perform basic file handling with iRODS?"
objectives:
- "connect to iRODS via the Python API with some security considerations"
- "upload/download data from iRODS"
- "create collections and access all objects in collections"
- "adding metadata to objects and collections"
- "querying for data based on metadata"
keypoints:
- "iRODS Python API"
- "Everything is an object"
---

You will learn how to interact with iRODS via the python API. In this module we will explore the API in interactive mode. 
You will:
- Up and download data
- Up and download data collections
- Add and edit metadata
- Set Accession control lists for data objects and collections


## Connect to iRODS

The module *getpass* asks for passwords without printing the input on screen. With en encoding function we prevent that the variable contains the plain password.
~~~
import getpass
pw = getpass.getpass().encode('base64')
~~~
{: .language-python}

# Standard Files

When the lesson repository is first created,
the initial author should create a `README.md` file containing
a one-line explanation of the lesson's purpose.

The [lesson template]({{ site.template_repo }}) provides the following files
which should *not* be modified:

*   `CONDUCT.md`: the code of conduct.
*   `LICENSE.md`: the lesson license.
*   `Makefile`: commands for previewing the site, cleaning up junk, etc.

## Starter Files

The `bin/lesson_initialize.py` script creates files that need to be customized for each lesson:

`CONTRIBUTING.md`
:   Contribution guidelines.
    The `issues` and `repo` links at the bottom of the file must be changed
    to match the URLs of the lesson:
    look for uses of `FIXME`.

`_config.yml`
:   The [Jekyll][jekyll] configuration file.
    This must be edited so that its links and other settings are correct for this lesson.
    *   `carpentry` should be either "dc" (for Data Carpentry), "lc" (for Library Carpentry), or "swc" (for Software Carpentry).
    *   `title` is the title of your lesson,
        e.g.,
        "Defence Against the Dark Arts".
    *   `email` is the contact email address for the lesson.

`CITATION`
:   A plain text file explaining how to cite this lesson.

`AUTHORS`
:   A plain text file listing the names of the lesson's authors.

`index.md`
:   The home page for the lesson.
    1.  It must use the `lesson` layout.
    2.  It must *not* have a `title` field in its [YAML][yaml] header.
    3.  It must open with a few paragraphs of explanatory text.
    4.  That introduction must be followed by a single `.prereq` blockquote
        detailing the lesson's prerequisites.
        (Setup instructions appear separately.)
    5.  That must be followed by inclusion of `syllabus.html`,
        which generates the syllabus for the lesson
        from the metadata in its episodes.

`reference.md`
:   A reference guide for the lesson.
    The template will automatically generate a summary of the episodes' key points.
    1.  It must use the `reference` layout.
    2.  Its title must be `"Reference"`.
    3.  Its permalink must be `/reference/`.
    4.  It should include a glossary, laid out as a description list.
    5.  It may include other material as appropriate.

`setup.md`
:   Detailed setup instructions for the lesson.
    Note that we usually divide setup instructions by platform,
    e.g.,
    include level-2 headings for Windows, macOS, and Linux
    with instructions for each.
    The [workshop template]({{ site.workshop_repo }})
    links to the setup instructions for core lessons.
    1.  It must use the `page` layout.
    2.  Its title must be `"Setup"`.
    3.  Its permalink must be `/setup/`.
    4.  It should include whatever setup instructions are required.

`_extras/about.md`
:   General notes about this lesson.
    This page includes brief descriptions of The Carpentries,
    and is a good place to put institutional acknowledgments.

`_extras/discussion.md`
:   General discussion of the lesson contents for learners who wish to know more:
    This page normally includes links to further reading
    and/or brief discussion of more advanced topics.
    1.  It must use the `page` layout.
    2.  Its title must be `"Discussion"`.
    3.  Its permalink must be `/discuss/`.
    4.  It may include whatever content the author thinks appropriate.

`_extra/figures.md` and `_includes/all_figures.html`
:   Does nothing but include `_includes/all_figures.html`,
    which is (re)generated by `make lesson-figures`.
    This page displays all the images referenced by all of the episodes,
    in order,
    so that instructors can scroll through them while teaching.

`_extras/guide.md`
:   The instructors' guide for the lesson.
    This page records tips and warnings from people who have taught the lesson.
    1.  It must use the `page` layout.
    2.  Its title must be `"Instructors' Guide"`.
    3.  Its permalink must be `/guide/`.
    4.  It may include whatever content the author thinks appropriate.

## Figures

All figures related with the lesson **must** be placed inside the directory `fig` at the root of the project.

{% include links.md %}

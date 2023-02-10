# HACBS Documentation Contributing Guide

HACBS (Stonesoup Cloud Build Services) is an effort to automate
build and delivery of Red Hat products. HACBS is a CD (Continuous
Delivery) platform that is run internally at Red Hat. This repository
contains the HACBS documentation in AsciiDoc format.

AsciiDoc is a plain text documentation syntax, also known as a mark-up
language, for text files. AsciiDoc is rendered as HTML automatically by
web browsers, so the files can be viewed as formatted text via the GitLab
repository URL.

## Development

For active maintenance/development of the HACBS documentation, developers
should create a
[fork](https://docs.gitlab.com/ee/user/project/repository/forking_workflow.html#creating-a-fork)
of the HACBS documentation repository. Updates are performed in the forked
repository and, when changes are ready for review, submitted as
[merge requests](https://docs.gitlab.com/ee/user/project/merge_requests/creating_merge_requests.html)
to the upstream repository. Developers are encouraged to create task
specific branches in their forked repositories, but merge request should
always target the default branch of the
[HACBS repository](https://gitlab.cee.redhat.com/HACBS/documentation).

### Rendering Individual Pages

To render individual AsciiDoc pages for review,
use the `asciidoctor` software to generate HTML files.

To install `asciidoctor` on Fedora or RHEL:

```bash
sudo dnf install -y asciidoctor
```

To create HTML files on your local system:

```bash
asciidoctor <name>.adoc
```

There are also Integrated Development Environments (IDEs) that will render
AsciiDoc pages while editing. Check the documentation of your specific IDE
for information on enabling AsciiDoc rendering.

**IMPORTANT:**
> Final rendering of the HACBS documentation is done with Antora,
> which overrides some of the AsciiDoctor formatting. Use the instructions
> below to render the entire site for a final check of any changes to the
> documentation.

### Rendering the Entire Site

To locally render the entire site, navigate to the root of the repository
and run:

```bash
npm install
npm run dev
```

Then visit http://127.0.0.1:8080.


The site rendered by Antora with the commands above is not dynamic, the pages
will not be re-rendered automatically if the AsciiDoc files change. You can
set up watchmedo from watchdog to rerun the server after every AsciiDoc
file change using the command below. Be aware, the server will take a few
seconds to restart every time a file changes.

```bash
python3 -m venv venv
source venv/bin/activate
python -m pip install watchdog[watchmedo]
watchmedo auto-restart --patterns="*.adoc" --recursive npm run dev
```

## AsciiDoc Mark-Up Language References

The [HACBS Documentation Style Guide](https://HACBS.pages.redhat.com/documentation/developers/documentation_style_guide.html)
describes the formatting conventions used for HACBS AsciiDoc files.
It also contains links to the other AsciiDoc reference material that will
be useful to developers working on the AsciiDoc files.

The [AsciiDoc Writer's Guide](https://asciidoctor.org/docs/asciidoc-writers-guide/)
"provides a gentle introduction to AsciiDoc".
It introduces the syntax in an easy to understand narrative with examples.

The [AsciiDoc Syntax Quick Reference](https://asciidoctor.org/docs/asciidoc-syntax-quick-reference/)
contains concise information on all the syntax available in AsciiDoc.

The [Red Hat Conventions for AsciiDoc Mark-up](https://redhat-documentation.github.io/asciidoc-markup-conventions/)
contains the Red Hat specific conventions for documentation written in
AsciiDoc.

## Documentation Standards Links

- [IBM Documentation Style Guide](https://www.amazon.com/IBM-Style-Guide-Conventions-Writers-dp-0132101300/dp/0132101300)
- [Glossary of Terms and Conventions for Red Hat Product Documentation](https://gitlab.cee.redhat.com/ccs-internal-documentation/glossary-of-terms-and-conventions-for-product-documentation)
- [Red Hat Modular Documentation Reference](https://redhat-documentation.github.io/modular-docs/)

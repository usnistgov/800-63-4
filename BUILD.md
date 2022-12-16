# Build Instructions

This document source is formatted with Markdown and uses Docker to enable building the final documents in both HTML and PDF formats.

To build the HTML website and run a local server, use the command:

~~~
docker-compose up
~~~

This will start a local Jekyll server which will be available on <http://localhost:4000/800-63-4/>.

To build the PDF documents, use the command:

~~~
docker-compose -f docker-compose-pdf.yml up
~~~

This will build a set of PDF files:

- `_pdf/SP800-63-4/SP800-63-4.pdf`
- `_pdf/SP800-63A-4/SP800-63A-4.pdf`
- `_pdf/SP800-63B-4/SP800-63B-4.pdf`
- `_pdf/SP800-63C-4/SP800-63C-4.pdf`

To build only a single document, set the `PDFTARGET` environment variable to the volume name. For example, to build only SP800-63B-4, use the command:

~~~
PDFTARGET='SP800-63B-4' docker-compose -f docker-compose-pdf.yml up
~~~

The source of each document is in a different source directory:

* `_sp800-63` contains SP 800-63-4, Digital Identity Guidelines
* `_sp800-63a` contains SP 800-63A-4, Enrollment and Identity Proofing Requirements
* `_sp800-63b` contains SP 800-63B-4, Authentication and Lifecycle Management
* `_sp800-63c` contains SP 800-63C-4, Federation and Assertions

Within these directories, each section of the document has its own source file.

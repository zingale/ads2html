# ads2html

This is a simple parser that will take a file of bibtex or a list of
ADS URLs and return a list of `Paper` objects that have the
bibliographic information in a convinent form for outputting to HTML.

Note: this requires python 3


## Working with a file containing bibtex

You can provide a file containing the bibtex for each paper directly from
ADS.  You will need to add an additional field, `subject`, that will be
used for subject classication sorting.  This can be assigned anything you
please.

```
import parser
papers = parser.parse_bibfile("papers.bib")

for p in papers:
    t, o, l = p.jstring()
    print(t, o, l)
```


## Working with a file containing ADS links

Your text file should be of the form:
```
subject: ads-url-to-abstract
```

E.g.,
```
algorithm: http://adsabs.harvard.edu/abs/2015ApJS..216...31Z
```

The paper ID will be obtained from the link and then the bibtex
will be directly downloaded from ADS.  The rest of the procedure
works the same:

```
import parser

papers = parser.parse_urlfile("castro-papers.txt")

...
```

## Example

The example `write_papers_html.py` will demonstrate how to generate an
HTML table, sorted by subject, from a list of ADS URLs.  This example
is from the Castro website: https://boxlib-codes.github.io/Castro/papers.html


# science-utils

A collection of scripts that will be useful for scientists (and
possibly others).

## spot-conflicts

`spot-conflicts` is a tool to help spot potential conflicts of
interest when members of a panel of reviewers have to evaluate a
series of candidates. Just prepare two plain text files containing the
list of candidates (one per line) and of reviewers (one per line too),
and run:

    ~ spot-conflicts reviewers.txt candidates.txt 

This command will list the papers candidates have published together
with reviewers, helping to spot potential conflicts of interest. The
articles are links to the pubmed page.

Full example (relying on Unix-like shell), with my PhD advisor:

    ~ echo fourmond > candidates.txt
    ~ echo leibl > reviewers.txt 
    ~ spot-conflicts candidates.txt reviewers.txt 
    Symplifying leibl to leibl
     -> found 188 publications
    Symplifying fourmond to fourmond
     -> found 41 publications

    Dealing with fourmond:
     -> article id 17602558 clashes with: leibl
     -> see more at http://www.ncbi.nlm.nih.gov/pubmed/17602558
    Found 1 potential clashes
     - leibl (abbreviated as leibl)

The program needs [perl](https://www.perl.org/).

### Caveats

 * it uses only [Pubmed](https://www.ncbi.nlm.nih.gov/pubmed) to find
   articlesand will therefore be useless to communities whose papers
   are absent from Pubmed;
 * the names in the files should be presented as `LastName
   FirstName`. For now, `FirstName` is **stripped**, so you may have a
   lot of false positives if the last name is common.
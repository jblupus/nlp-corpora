# nlp-corpora

![](https://img.shields.io/badge/docs-errors-red.svg?longCache=true&style=flat)
![](https://img.shields.io/badge/built-7/4/18-blue.svg?longCache=true&style=flat)

UW NLP maintains a repository of corpora for internal UW use on the UW CSE
department fileserver at `/projects/nlp-corpora/`.

The main purpose of this document is to provide a live, browsable index of all
of the corpora. Below that are instructions for accessing the corpora and
proposing new additions.

## Live Status

Below is the live status of the corpora, updated daily ([legend
below](#table-legend)).

dirname | desc | size | status
--- | --- | --- | ---
byu-coca | https://corpus.byu.edu/coca/ | 6.0G | ✔
byu-coha | https://corpus.byu.edu/coha/ | 4.4G | ✔
byu-now | https://corpus.byu.edu/now/ | 85G | ✔
deepbank | This is version 1.1 of the DeepBank corpus contains HPSG and MRS | 665M | ✔
fanfiction | This is a corpus of 1.25 billion lines of fan fiction text. | 164G | ✗
gigaword-en-5 | English Gigaword Fifth Edition | 33G | ✔
google-surface-ngrams | Google surface ngrams (web 1T 5-gram v1) | 25G | ✔
google-syntax-ngrams | English Google Syntax Ngrams (v20120701) | 319G | ✔
gutenberg-en | English Gutenberg. | 106G | ✗
nyt-annotated | The New York Times Annotated Corpus | 3.1G | ✔
penn-treebank-revised | English News Text Treebank: Penn Treebank Revised | 16M | ✔
roc-stories | ROCStories Corpus. | 27M | ✔
toronto-books | The Toronto Books corpus. | 8.8G | ✔




## Documentation

### Using the corpora

Accessing the nlp-corpora requires UW CSE department server access (e.g., to
the machines `{recycle,bicycle,tricycle}@cs.washington.edu`) so that they can
view the department filesystem. The nlp-corpora directory is located on the
department filesystem at `/projects/nlp-corpora/`. Anyone with a UW CSE account
can log onto the department servers and view the files there. (For those
without a UW CSE account, see the section below.)

The corpora are meant to be read-only so that they stay in a known, clean
state. To work with files from the corpora, please copy them to a local
directory, e.g., with `scp`.

### Corpus structure

One of the goals of this project is to have a consistent directory structure
across all of the corpora we track to give a smooth experience browsing through
them. There is a detailed description of this structure [below](#corpus-structure).

### Adding a new corpus

Fill out this
[form](https://docs.google.com/forms/d/1SBPXlJ8zsE1kbVr6csE3d9XIaW9pCfvOkmH9kD6vEv8/viewform)
and we will work with you to add a new corpus to the repository.

### Restricted access

Some corpora require signing a form and sending it to the authoring institution
to be cleared for access. To honor these requests, we restrict access to
corpora for which this is required by narrowing the unix group that has read
privileges.

Instructions for streamlining this process are coming soon. In the mean time,
please open a github issue to request access to a restricted corpus.

### Access outside UW CSE

Accessing the corpora requires a UW CSE unix account. Anyone can receive a free
UW CSE guest account by having a UW CSE faculty or staff [sponsor
them](https://sponsor.cs.washington.edu/). Despite the name "sponsor," this is
absolutely _free_ for both parties. Guest accounts last up to two years and can
be renewed indefinitely. This is the way to grant NLP friends in EE and
linguistics access to nlp-corpora.


## Corpus structure

Inside the `/projects/nlp-corpora/` directory, there should only be directories
for corpora.

Each corpus directory `<name>` should have the following format:

```
<name>
├── original/
│   └── ...
├── processed/
│   └── ...
└── README.md
```

No other top-level contents in the corpus directory is allowed.

Each of the components should be as follows:

### `original/`

_Optional_

The `original/` subdirectory should contain the source material in the most
raw, unprocessed form possible. If the source material was downloaded as a
tarball, it should be that tarball. If it was downloaded as a set of files
comprising a dataset, it should be those files. If it was scraped from a
website, it should be the raw output of the scraping command (e.g., `curl` or
`wget`).

This may not exist for all corpora, but it is preferred to exist if possible.

### `processed/`

_Optional_

The `processed/` subdirectory should contain only subdirectories, no files.
Each subdirectory should be a succinct name for the type of processing that its
contents underwent. For example, if many text files were cleaned and joined
into one, `txt`, would be an appropriate name. If tokenization was applied,
`tkn` would be an appropriate name.

Details for all subdirectories within `processed/` must be provided in the
`README.md` file (more information on this below).

### `README.md`

_Required_

The `README.md` file is required because it provides all documentation about
the data source.

In general, it should have the following format:

```
# (tile of the corpus)

(Short description of the corpus.)

(How the corpus was acquired (including the URL or the contents of the script).)

(When the corpus was acquired.)

(For each subdirectory in "processed/" (if any exist), a description of how
that directory was created. Optimal is a script (or a link to a specific
version of a script). Also acceptable is an English description. For example,
if it was tokenized, which tokenizer was used, and which version of that
software.)
```



## Bugs / questions / contributions

For any bugs or questions, please open a GitHub issue on this repository (top
of the webpage).

To help contribute to this project, please check out the [backend
repository](https://github.com/mbforbes/nlp-corpora-backend) and open issues or
pull requests there.



## Maintainers

- [Max Forbes](https://github.com/mbforbes)

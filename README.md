# Documenation CI

> CI Process for Engineer-led Documentation

## Overview

### CI Structure

```
├── CI
│   ├── linkchecker
│   │   └── link_check_conf.json
│   ├── markdownlint
│   │   ├── lint-base-style.yml
│   │   └── lint-info-style.yml
│   ├── requirements.txt
│   ├── scripts
│   │   ├── README.md
│   │   ├── run_job.sh
│   │   ├── test_all.sh
│   │   ├── test_build.sh
│   │   ├── test_guidelines.sh
│   │   ├── test_links.sh
│   │   └── test_markdown_syntax.sh
│   └── vale_styles
│       ├── Besu
│       │   └── Acronyms.yml
│       └── Microsoft
│           ├── AMPM.yml
│           ├── Accessibility.yml
│           ├── Acronyms.yml
│           ├── Adverbs.yml
│           ├── Auto.yml
│           ├── Avoid.yml
│           ├── Backend.yml
│           ├── ComplexWords.yml
│           ├── Contractions.yml
│           ├── Dashes.yml
│           ├── DateFormat.yml
│           ├── DateNumbers.yml
│           ├── DateOrder.yml
│           ├── Ellipses.yml
│           ├── FirstPerson.yml
│           ├── Foreign.yml
│           ├── Gender.yml
│           ├── GenderBias.yml
│           ├── GeneralURL.yml
│           ├── HeadingAcronyms.yml
│           ├── HeadingColons.yml
│           ├── HeadingPunctuation.yml
│           ├── Headings.yml
│           ├── Hyphens.yml
│           ├── LICENSE
│           ├── Negative.yml
│           ├── Ordinal.yml
│           ├── OxfordComma.yml
│           ├── Passive.yml
│           ├── Percentages.yml
│           ├── Quotes.yml
│           ├── RangeFormat.yml
│           ├── RangeTime.yml
│           ├── Ranges.yml
│           ├── Semicolon.yml
│           ├── SentenceLength.yml
│           ├── Spacing.yml
│           ├── Suspended.yml
│           ├── Terms.yml
│           ├── URLFormat.yml
│           ├── Units.yml
│           ├── Vocab.yml
│           ├── We.yml
│           ├── Wordiness.yml
│           ├── meta.json
│           └── vocab.txt
├── README.md
├── package.json
├── readthedocs.yml
└── vcs.xml
```

## Doc quality testing scripts

Use the scripts in this directory to run CircleCI jobs on your local machine before pushing your work

## Requirements

- Install the [Circle CI local CLI](https://circleci.com/docs/2.0/local-cli/)
- Install [Docker](https://docs.docker.com/install/).

## Running the scripts

Go to the besu-doc project root directory and run one of the following scripts:

- `CI/scripts/test_build.sh` runs the doc build with MkDocs.
- `CI/scripts/test_guidelines.sh` tests the doc with Vale and our custom rules.
- `CI/scripts/test_links.sh` tests the internal and external links in the doc. If a link is
  incorrect or the targeted web page is unavailable (for external sites), the test will fail and
  display the faulty link.
- `CI/scripts/test_markdown_syntax.sh` tests the Markdown syntax for issues. Sometimes they are not visible
  but making sure the markdown is correct helps to make it readable and bug free.
- `CI/scripts/test_all.sh` runs all the tests in one pass.

## Known issues

You will notice messages like:

```bash
====>> Saving Cache
Error:
Skipping cache - error checking storage: not supported

Step failed
```

This is normal. Circle CI doesn't support some of the features the server version does. Ignore them.

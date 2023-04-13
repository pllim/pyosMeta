# PyOS Consolidate Contributor Data & Update Review Metadata

This repo contains a small module and some scripts that parse through GitHub repos in the pyOpenSci organization.

## Rate limiting

Rate limiting - how to handle this...

## Update contributors across repositories

The contributors script parses data from:

TODO: check which repos we actually are parsing...

- software-review repo
- python-package-guide repo
- peer-review-guide repo
- software-review repo
- examplepy repo

The first script updates contributor data by:

1. Grabbing each contributor `.json` file generated by the all-contributors bot in each repository
2. Parsing the website contributors.yml from the website.
3. Adding all contributors identified in step 1 to the website yaml file.
4. Finally it updates contributor metadata using each user's GitHub profile to get website, location, twitter handle, etc (if it is available)

This script allows pyOpenSci to quickly update the website contributor list with the current list of contributors. It also ensures contributor metadata is current (or up to date with what the user is maintaining on their GitHub user page)

## Update contributors across repositories

To update package and review metadata you can
use `parse_issue_metadata.py`.

This script:

- Parses each issue that has a label of 6/`pyOS-approved 🚀🚀🚀`.
- Grabs crucial metadata including the reviewers and editors for each.
- Finally it grabs package metadata to add to the packages.yml file including stats around last commit date, package stars and other github metrics.
- It should also add people who have participated in peer review who are NOT listed currently in the website contributors.yml file

python3 parse_issue_metadata.py

## Using this

Create environment:

`mamba env create -f environment.yml`

```
❯ hatch new pyosMeta2
pyosmeta2
├── pyosmeta2
│   ├── __about__.py
│   └── __init__.py
├── tests
│   └── __init__.py
├── LICENSE.txt
├── README.md
└── pyproject.toml
```

Hatch also seems to create an init and a about that has a standard version.

# How do i use Hatch with a conda environment?

looks like i have to install a plugin for this... wondering if i want to go with PDM for now? Or Poetry?

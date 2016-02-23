# Coding Conventions

We establish coding conventions in order to produce work that is legible, consistent and predicatble. By maintaing uniformity in our styles it we strive to share code more efficiently, minimizing time required to understand nuances. Please do your part to adhere to the conventions set forth in this manual, and kindly notify others — ideally in comments in pull requests — where there are deviations.

There will be legacy files, generated prior to this manual's creation, that do not conform to our conventions. If you're working on an older project, be consistent with what's already there.


## Repository Naming
__Repo names should be kebab-case:__

ACS Cancer Atlas should be `acs-cancer-atlas`


__Articles and prepositions should be ommitted from names__

Bank of America Heatmap should be `bank-america-heatmap`


__When a repository is for a company's primary web presence, use the company name as the repo name.__

Chicago Community Trust should be `chicago-community-trust`

__If creating a microsite or product for a client, prefix the repo with the company's name (acronmys preferred for longer companies) and describe the project.__

Chicago Community Trust email templates should be `cct-email-templates`


## File Naming


## Git Commits

Commit messages are comprised of 3 parts:

* A short description of what is contained in the commit (max line-length 50 char)
* A longer description of changes contained in commit (max line-length 72 char)
* A footer that links to relevant pivotal/git issues

A git client like gitx may provide guidelines for adhereing to a max-length.

![](_doc/max-line-length.png)

Example:
```
Fixed bug where user can't signup.

Users were unable to register if they hadn't visited the plans
and pricing page because we expected that tracking
information to exist for the logs we create after a user
signs up.  I fixed this by adding a check to the logger
to ensure that if that information was not available
we weren't trying to write it.

[Fixes #2873942]
```

[Further reading](http://ablogaboutcode.com/2011/03/23/proper-git-commit-messages-and-an-elegant-git-history/)



## Pull Requests
Development for features should be done on separate branches and merged in via pull requests. PRs should be assigned to at least one other developer and approved prior to merge, but merging should be done by the developer submitting the request.


## Languages
- [JavaScript](/style/javascript.md)
- [HTML](/style/html.md)
- [SCSS](/style/scss.md)
- [Python](/style/python.md)
- [PHP](/style/php.md)

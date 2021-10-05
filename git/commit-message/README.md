# Alternative Commit Message Format (version 0.9)

## What is it?
This is a proposal of labels to be used in commit messages. The goal is to identify easily the different types of changes in a repo.

## Commit Message rules

Common layout for a commit message (based on [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/#summary))

```
<type>[optional scope]: <description>

[optional body] - used to explain the what and why of a commit, not the how. Wrap the body at 72 characters in each line.

[optional footer(s)] - used to reference issue tracker IDs
```

The ***header*** is **mandatory** and the scope of the header is optional.

Any line of the commit message cannot be longer 72 characters! This allows the message to be easier to read on GitHub as well as in various git tools.

The footer should contain a closing reference to an issue if any.

A ***scope*** may be provided to a commit’s type, to provide additional contextual information and is contained within parenthesis, e.g., `feat(parser): add ability to parse arrays.`

#### Revert

If the commit reverts a previous commit, it should begin with revert: , followed by the header of the reverted commit. In the body it should say: This reverts commit <hash>., where the hash is the SHA of the commit being reverted.

#### Subject desription (first line)
1. Prefix the line with an applicable label
2. Limit all the lines (subject included) to 72 characters
3. Use the imperative tone in the subject line
4. Separate subject from body with a blank line
5. Capitalize the subject line
6. Do not end the subject line with a period

#### Main tags and meaning for source code
**NOTE:** The first commit does not have a label, and the message always is "**Initial commit**" as convention.

* **core:** The most common day-to-day changes that are created while building a `feature`, that is, methods or classes that have been created, modified or removed, as well as modifications to method signatures or changes to return types .
* **feat:** Changes that introduce new feature to the codebase (this correlates with ***MINOR*** in [Semantic Versioning]).This is only used when you are doing a merge between a change-branch and source branch. Features may exclusively be targeted for the “master” branch.
* **fix**: A fix commit  patches a bug in your codebase (this correlates with ***PATCH*** in [Semantic Versioning]).
* **pkg:** Used when libraries, frameworks, packages  or modules are added.
* **ci:** Changes to the configuration files and scripts.
* **boost**: A code change that improves performance.
* **docs:** Used when writing documentation, formatting comments on code (no code change).
* **test:** Used when adding tests or refactoring tests (no production code change).
* **style:** Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc) and do not modify previous funcionality.
* **refactor:** A code change that neither fixes a bug nor adds a feature.
* **task:** Anything not covered by the above categories, e.g. rename or move files, add dataset, etc.  
* **BREAKING CHANGE:** A commit that has a footer BREAKING CHANGE:, or appends a ! after the type/scope, introduces a breaking core change (correlating with ***MAJOR*** in [Semantic Versioning]). A BREAKING CHANGE can be part of commits of any type.  

#### Body
Just as in the subject, use the imperative, present tense: "change" not "changed" nor "changes". The body should include the motivation for the change and contrast this with previous behavior.

#### Footer
The footer should contain any information about Breaking Changes and is also the place to reference GitHub issues that this commit Closes.

Breaking Changes should start with the word BREAKING CHANGE: with a space or two newlines. The rest of the commit message is then the description of the change, justification and migration notes.

[Semantic Versioning]: https://semver.org/

## REFERENCES

1. [How to Write a Git Commit Message](http://chris.beams.io/posts/git-commit/#why-not-how) Chris Beams
2. [TYPO3 CMS](http://wiki.typo3.org/CommitMessage_Format_(Git))
3. [Atom](https://atom.io/docs/v0.186.0/contributing)
4. [Karma](http://karma-runner.github.io/0.8/dev/git-commit-msg.html)
5. [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/#summary)
6. [Angular](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#-commit-message-guidelines)
7. [AngularJS Git Commit Message Conventions](https://docs.google.com/document/d/1QrDFcIiPjSLDn3EL15IJygNPiHORgU1_OOAqWjiDU5Y/edit#)
8. [A Note About Git Commit Messages](https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)

-------------
This document was last modified on : July 9th, 2020.

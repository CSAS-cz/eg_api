#EG George API documentation

##Storage

The API specification is stored in files in a [blueprint format](http://apiary.io/blueprint) - this is an easily editable text format based on [Markdown format](http://daringfireball.net/projects/markdown/syntax).
These files are stored in GIT repository on Github.
The repository has two branches: 

- working_branch contains multiple small blueprint files - grouping related resources, endpoints 
- merged_branch containing one file produced by merging of all files from the working branch

The group specification is stored this way, editing of API documentation is done only by editing working branch blueprint files.

##Generating a documentation

The merged file from the second branch is synchronized with the Apiary tool - as a result there is a documentation generated and it is possible to use all the other features of the Apiary as mocking or validation of the API.

Once a change to the API specification is pushed to the GIT repository working branch an additional script should be run (In future maybe it will be part of a post-push hook). This script performs these steps:

- merges all the files from the working branch (removes technical header preambules)
- generates changelog from commit messages and prepends to this file

At the moment generated file must be pushed manually to the second branch (This job will be automated by a post-push hook). This file should be only generated, never edited. The API editation must be always performed on the files in the working repository.

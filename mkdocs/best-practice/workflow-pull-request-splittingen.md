---
category: github-workflow
sub_category_1: pull-request-splitting
language: en
tags:
- git
- github
- best-practice
- pull-request
- pull-request-splitting
---

## Sample workflow

Here's a sample workflow for creating and managing blog posts with pull request splitting:

``` mermaid
graph TD
	A((master-branch)) -- create --> B((blog-db-migration))
	A -- create --> C((blog-list-page))
	A -- create --> D((blog-create-entry))
	A -- create --> E((blog-edit-entry))
	B -- merge --> A
	C -- merge --> A
	D -- merge --> A
	E -- merge --> A
	B -- merge --> C
	C -- merge --> D
	D -- merge --> E
```

1.  Create a new branch from the master branch with a meaningful name such as "blog-db-migration" for the migrations.
	1.  Perform all necessary steps to implement and test the migrations.
2. Create another branch from the current master branch with a name like "blog-list-page" for listing the blog entries.
	1. Add the previous branch "blog-db-migration" to this new branch "blog-list-page" and perform all the necessary steps to implement and test the listing of blog entries.
3. Create another branch from the current master branch with a name like "blog-create-entry" for adding new blog entries.
	1. Merge the previous branch "blog-list-page" into this new branch "blog-create-entry" and perform all necessary steps to implement and test adding new blog entries.
4. Create another branch from the current master branch with a name like "blog-edit-entry" for editing existing blog entries.
	1. Merge the previous branch "blog-create-entry" into this new branch "blog-edit-entry" and perform all necessary steps to implement and test editing of existing blog entries.

!!! warning
	It is important that each pull request functions independently and contains only the necessary changes. Therefore, each pull request should only be evaluated if the previous pull request has already been merged and the pull request under review has been updated as a result. Failure to do so can result in too many files being displayed in the pull request for review, which can make the review more difficult. It is also important to indicate in each pull request what other pull requests it builds on to ensure that they are reviewed and merged in the correct order.

!!! tip
	Stashes can be used as a workaround to organize changes in different branches

	If you notice while working that you have made changes in the current branch, but they should actually be assigned to another branch, you can use stashing as a workaround. You can save the files in question in a stash, so that you can assign them to the correct branch later. This way you can avoid that changes accidentally end up in the wrong branch and thus disrupt the workflow. After creating the stash, you can later distribute it to the appropriate branch and delete the stash.

!!! tip
	It is useful to periodically synchronize the code with the main branch to ensure that there are no conflicts when the pull requests are to be memoized.

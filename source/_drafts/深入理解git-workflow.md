---
title: 深入理解git workflow
tags:
  - git
id: 1748
categories:
  - 版本控制
---

If you’re fighting Git’s defaults, ask why.

Treat public history as immutable, atomic, and easy to follow. Treat private history as disposable and malleable.

The intended workflow is:

Create a private branch off a public branch.
Regularly commit your work to this private branch.
Once your code is perfect, clean up its history.
Merge the cleaned-up branch back into the public branch.
> git checkout master
> git checkout -b cleaned_up_branch
> git merge --squash private_feature_branch
> git reset

source: http://sandofsky.com/blog/git-workflow.html
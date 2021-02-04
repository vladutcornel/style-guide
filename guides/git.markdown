---
layout: page
title: Git guidelines
---

There is no competition anymore. Git is now the industry standard for code versioning. 

There are some things to consider when using it:

Do not follow this guide
------------------------
If you are joining an existing project and team, chances are there are already style guides that your team follows.
Ask your Team Leader about them. Only if there aren't any, or you feel comfortable in suggesting changes,
ask them if they are willing to follow this guide.

Do not mix projects
-------------------
As much as possible, one Git repository should hold a single unbreakable project.

Have a consistent branching strategy
------------------------------------
There are a few different strategies to naming your branches. You have to pick one that makes sense to you, and your team, and stick with it.  
One example is [Git Flow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) (note you can use the branching strategy manually without the Git extension, if you want to).  

Make as many unbreakable commits
--------------------------------
A single commit should do a single unbreakable change. If multiple changes were made to a single file, commit line-by-line. Git GUIs like GitKraken or Git-Cola allow you to commit single lines or hunks of changes.

Code should be stable after each commit
---------------------------------------
If anyone runs the code at the commit, it should work with no bugs

Commit message
--------------
The commit message I suggest is inspired by [Angular's](https://github.com/angular/angular/blob/master/CONTRIBUTING.md#-commit-message-format), but with some changes to make it generally more usable

```
<type>(<issue>): <short summary>
  |       |             |
  |       |              -> Summary in present tense. Not capitalized. No period at the end.
  |       |
  |        -> Optional issue number from any tracker you use.
  |
   -> Commit Type: wip|build|ci|docs|feat|fix|perf|refactor|test|...
```

If using GitLab or GitHub built-in issue trackers, the issue number should be prefixed by `#` (e.g. `#1234`). For other issue trackers, such as Jira, use the naming convention from there (e.g. in Jira: `ABC-1234`).

Push anything you have at EOD
-----------------------------
At the end of each day, regardless of how far you are with your changes, push anything you have to the cloud/online repository you are working with.  
Use `wip` (Work in progress) as the type if the change is not complete.

Why?  
You may lose access to your computer, for various reasons. If you didn't push your changes, they may be lost. 

Remove or Amend `wip` commits
-----------------------------
Once changes are complete, remove the "Work in progress" commits, and replace them with proper commits. 
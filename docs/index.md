# Git, GitHub and GitKraken

[![](https://imgs.xkcd.com/comics/git.png)](https://xkcd.com/1597/)

* Table of Contents
{:toc}

Notes on the Workshop [GitKraken : Zero to Hero](https://srse-git-github-zero2hero.netlify.app/).

## GitHub Pages

The web-page is published using [GitHub Pages](https://pages.github.com).

1. Create an initial `index.md` and add text to it (in [Markdown](https://www.markdownguide.org)).
2. Commit and push your changes to your repository.
3. Visit your pages GitHub repository and go to `Settings`.
4. Under `Pages` select the branch where `index.md` has been created and its location (by default these are `main` and
`root`).
5. Save these changes.

You should then have a green box appear with the message "_Your site is published at..._" with a URL pointing to its
location.

You can update the theme of the site using the `Theme Chooser` on the same page. As you can see I've opted for the
`Hacker` theme.

Useful references for Markdown Syntax are...

* [Basic Syntax](https://markdownguide.org/basic-syntax)
* [Extended Syntax](https://markdownguide.org/extended-syntax)
* [Cheatsheet](https://markdownguide.org/cheat-sheet)

## Collaboration

1. Make a fork of
   [RSE-Sheffield/collaborative_github_exercise](https://github.com/RSE-Sheffield/collaborative_github_exercise/fork) by
   clicking on the `Fork` button at the top-right. This copies the fork to your own account.
2. Clone the repository to your local computer by clicking on `Code`, copying the URL and typing...

```bash
git clone git@github.com:ns-rse/collaborative_github_exercise.git
```

3. Make a copy of `params/project_tmpl.R` into `params/some_unique_name.R` and start editing it.

4. Add a value between `0` and `5` for `sig2`.

5. Add a value for `species.name <- 'some_unique_name'`.

6. Change the `color <- "cyan"` (a list of possible colours are available [here](http://www.stat.columbia.edu/~tzheng/files/Rcolor.pdf))

7. Save, commit and push your changes to _your_ fork of the repository.

### Create a Pull Request

Now create a pull request from your fork on GitHub to the `master` (or `main`) branch of the base repository from which
the fork was made (`RSE-Sheffield/collaborative_github_exercise`). To do this...

1. Click on `Pull Request`.

2. Ensure the target is `RSE-Sheffield/collaborative_github_exercise` on branch `master` and the source is
  `<your-account>` and the branch is `master`.

3. Add a commit message describing what is being added "_This commit is ..._" and a message for a more information.

4. Click on "_Create Pull Request_".

### Pull Requestes from GitKraken

From Git Kraken you can add a Remote source to your repository which makes it easier for you to track changes that have
been made to projects you have forked from. Branches can be aligned by dragging and dropping the icons from one branch
to another.

## Advanced Collaboration Through GitHub

The basis of this is the concept of "branches" where you work on an isolated set of the code that is known (or should)
work.

The basis for the work is the [RSE-Sheffield/python-calculator](https://github.com/RSE-Sheffield/python-calculator)
which one person should copy using the "_Use this template_" button to make a copy to their account. Then protect the
branch by...

1. _Settings > Branches_ and select teh `main` branch to _Require pull requst before merging_ and set a number fo
   _Require approvals_.

2. Next add _Settings > Collaborators_ and add your colleagues GitHub usernames.

3. The owner of the project should create a branch and modify `setup.cfg` with their details (author, author email,
   url, Bug Tracker url), save, commit and push. On first push the branch won't exist remotely and so the name will
   be set (GitKraken will ask this automatically, just as `git` does at the command line).

4. Pull requests can be made straight from Git Kraken, once made they need assigning to a team member who can then
   approve which will allow someone to merge the pull request.

5. We now create issues _Issues > New Issue_, for this exercise there are three issue templates and they are assigned to
   different individuals. They should use the checklist to go through each of the tasks before submitting pull requests
   which are then reviewed.

6. Mistakes that cause tests to error can arise, particularly for those unfamiliar with Python and these can be reviewed
   with feedback comments/suggestions.

7. If things are being done in parallel then it should result in a merge conflict that can then be resolved through
   GitHub. Once resolved the pull requests can be merged and the branches deleted.

8. Finally users can fast-forward their local copies.


## FAQ

These questions are recorded across three runs of the course so far to see what questions crop up.

## Git

### I got this error: "Push main: Push failed on refs/heads/main: push declined due to email privacy restrictions"

A quick fix to this is to visit the [GitHub Email Settings](https://github.com/settings/emails) and uncheck `Block
command line pushes that expose my email`. This is not ideal though as its exposes your email address. A better solution
in the long term (described in detail on
[StackOverflow](https://stackoverflow.com/questions/43378060/meaning-of-the-github-message-push-declined-due-to-email-privacy-restrictions))
is to...

1. visit the [GitHub Email Settings](https://github.com/settings/emails) and ensure `Keep my email address private` is
   checked.
2. Copy the `{ID}+{username}@users.noreply.github.com`.
3. Open a [GitKraken CLI](https://www.gitkraken.com/cli#) window.
4. Type `git config --global user.email {ID}+{username}@users.noreply.github.com` replacing `{ID}` and `{username}` with
   the values you copied from above, then hit `Enter`.
5. Amend the author of the previous commit with `git commit --ammend --reset-author`.
6. Push the amended git with either `git push` at the Command Line Interface or using the `Push` button in GitKraken
   Client.

### Can you delete changes?

You can but its complicated and there are many options available which will be contingent on what you want the commit
history to reflect, although typically most leave the commit history in place and add a new commit documenting the
changes.

You can `git reset` to roll the `HEAD` back to an earlier point (for more see [How To Use Git
Reset](https://www.w3docs.com/learn-git/git-reset.html)) or you can `git revert` to undo the changes introduced by a
specific commit (see [How To Use Git Revert](https://www.w3docs.com/learn-git/git-revert.html)). Other options include
using `git rm` to remove specific files from being tracked ([How To Use Git
RM](https://www.w3docs.com/learn-git/git-rm.html)) and `git rebase` to move and combine a series of commits ([How Tow
Use Git Rebase](https://www.w3docs.com/learn-git/git-rebase.html)).

It is possible to roll back a branch to any stage in the history of commits by using `git checkout <hash_id>` but this
will mean you are in a [Detached HEAD](https://www.w3docs.com/learn-git/git-checkout.html#detached-heads-27) state as
you are not at the `HEAD` of that branch. It is possible to reset which commit `HEAD` points to but it is a destructive
process and can cause a lot of problems and is not therefore recommended.

If you have not committed changes locally and only staged them you can delete or change anything, it will just unstage
the modified files and you can then stage and commit them again after making corrections.

### If I have multiple commits do I need to push them individually?

No a push can include multiple commits.

### Why do we need to 'stage'? / What's the benefit of `stage -> commit` instead of having a direct `commit`?

It is so that we can choose which changes to which files we wish to push at a given point in time. You may have a
project where you have modified 14 files on a branch you are working on but at this point in time half of those are
still experimental and not ready to be pushed. You therefore only stage the 7 files that are ready to be pushed, leaving
the others in place locally for inclusion in a later push.


## GitHub

### Can/should data be shared on GitHub?

Technically you can, but GitHub isn't really designed for sharing large files. Further there may be data governance
issues that cover your data. For more information on sharing your data see the [Sharing research data - Research Data
Management - The University Library - The University of Sheffield](https://www.sheffield.ac.uk/library/rdm/publish).


### Wouldn't it be more meaningful if it was named "new push request"?

It depends on your perspective. When you have made changes to a fork and you wish them to be incorporated into the
original repositories branch then from your point of view you are pushing, just as you do from local to GitHub.

From the perspective of the original maintainer they, as recipient, see it as "pulling" your changes into their
branch. Given the original is their branch and you are adding to it then the owners perspective takes precedence, hence
why its a request to "pull" your changes into their repository.

However, it's best not to worry too much about it, a "pull request" is a way of merging a branch into another branch in
a repository, and an opportunity to have a discussion about it before doing so.


### Can one skip forking, make a copy, and submit a PR?

You could but you may not always have permission to submit pull requests directly.

Also you should _never_ make changes directly to a `main` branch, you should always make them to a branch and then merge
that branch via a Pull Request. This helps protect the `main` branch from errors creeping in as Pull Requests get
reviewed. This is what forking is doing, its making a branch from the main repository for you to work on.

Many large code bases have a number of [GitHub Actions](https://github.com/features/actions) that carry out such tasks
as unit, and integration and regression tests, linting of code to ensure it complies to style guides, building and
releasing packages. This, along with careful code review of Pull Requests, helps ensure that newly submitted code does
not break software.

### Does Github not have a staging area?

Not when making edits directly to a single file online via GitHub as typically you are only changing a single file so
there is no need to choose which files to stage. However, rather than committing them directly to the branch you are
working on you do have the option to create a branch and pull request for your changes.


## GitKraken

### Will the trial period of GitKraken expiring be a problem? / How do I get GitKraken/GitHub pro account?

The 7-day trial period only refers to a short window where you get all of the paid features that are available to try
out. After this trial period expires you will still be able to use GitKraken and nothing in this course requires the
paid features, for more information on the different features see [GitKraken Client
Pricing](https://www.gitkraken.com/git-client/pricing).


If you are using a trial version of GitKraken for this course you won't encounter any problems. Longer term though you
will want to setup a GitHub account using your University email address which allows you to take advantage of their
[GitHub Campus Program](https://education.github.com/schools). If your account isn't already registered then you can
find instructions on how to do so at [Apply for an educator or researcher discount - GitHub
Docs](https://docs.github.com/en/education/explore-the-benefits-of-teaching-and-learning-with-github-education/use-github-in-your-classroom-and-research/apply-for-an-educator-or-researcher-discount).

Once you connect to this GitHub account through GitKraken you will automatically receive access to the full GitKraken
Client Stand-Alone through their [GitKraken Resources for Schools](https://education.github.com/schools), which is
contingent on your account being registered with GitHub Campus Program.


### Does GitKraken pick up files added directly to the local repository?

Yes Git and GitKraken are aware of what files are within the repository, and which files are being tracked and which
aren't and which files have changed since the last commit.

## Miscellaneous

### Will we be covering the command line interface? / How should I do this in the terminal?

No, the focus of this course is using GitKraken to interact with Git and GitHub, however the [Git
manual](https:git-csm.com/docs/user-manual.html) contains all the equivalent command line options.  There is `man git`
as well and each command has its own help page accessible with `git pull --help`, `git checkout --help` (generally its
`git <command> --help`). There are also a number of additional resources in the Links section below.

# Links

* [GitKraken : Zero to Hero](https://srse-git-github-zero2hero.netlify.app/)
* [GitHub Pages](https://pages.github.com)
* [Markdown](https://www.markdownguide.org)
* [Class Notepad](https://docs.google.com/document/d/1-CkHO417wtfJZ35X4q5tk_hcgP9W3mfEG5AsN2SIU1A/edit#)

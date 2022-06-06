# Git, GitHub and GitKraken

[![](https://imgs.xkcd.com/comics/git.png)](https://xkcd.com/1597/)

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

## Advanced Collaboation Through GitHub

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

### Can/should data be shared on GitHub?

Technically you can, but GitHub isn't really designed for sharing large files. Further there may be data governance
issues that cover your data. For more information on sharing your data see the [Sharing research data - Research Data
Management - The University Library - The University of Sheffield](https://www.sheffield.ac.uk/library/rdm/publish).

### Do you need to do anything with SSH/Auth/GPG tokens?

Not at the moment for this project.

### Can you delete changes?

You can but typically you make subsequent commits to revert changes.

### Will we be covering the command line interface?

No, we focus on using

### Does GitKraken pick up files added directly to the local repository?

Yes Git and GitKraken are aware of what is within the repository and which files are being tracked.

### Why do we need to 'stage'?

It is so that we can choose which changes to which files we wish to push at a given point in time.

### If I had multiple commits, do I need to click on a specific commit to push or will push send all commits to origin?

A single push can send multiple commits.

### What's the benefit of `stage -> commit` instead of having a direct `commit`?

Staging allows a few changes to be added, rather than committing all changes at the same time.

### Does Github not have a staging area?

Not when making edits directly to a single file online as typically you are only changing a single file, however
although you do have the option to create a branch and pull request for your changes.

# Links

* [GitKraken : Zero to Hero](https://srse-git-github-zero2hero.netlify.app/)
* [GitHub Pages](https://pages.github.com)
* [Markdown](https://www.markdownguide.org)
* [Class Notepad](https://docs.google.com/document/d/1-CkHO417wtfJZ35X4q5tk_hcgP9W3mfEG5AsN2SIU1A/edit#)

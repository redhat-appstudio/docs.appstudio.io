# App Studio documentation

App Studio is an effort to automate build and delivery of Red Hat products. With App Studio, you have access to single, simple workflow for developing, testing, and releasing containerized applications while ensuring compliance with enterprise security standards.

## App Studio documentation links

* [Getting started guide](https://redhat-appstudio.github.io/docs.appstudio.io/Documentation/main/getting-started/get-started)
* [User documentation](https://redhat-appstudio.github.io/docs.appstudio.io/Documentation/main)
* [Upstream landing page](https://redhat-appstudio.github.io/appstudio.docs.ui.io/)
<!-- * [Schema Documentation](https://red-hat-stone-soup.pages.redhat.com/stonesoup-documentation/schema/index.html) -->
<!-- * [Architecture Overview](https://red-hat-stone-soup.pages.redhat.com/stonesoup-documentation/architecture/index.html) -->

## External links

* [HACDOCS project in JIRA](https://issues.redhat.com/projects/HACDOCS/summary)
* [HACBS hub on Confluence](https://docs.engineering.redhat.com/pages/viewpage.action?pageId=256849149)

## App Studio contact information

* [App Studio documentation home page](https://redhat-appstudio.github.io/appstudio.docs.ui.io/)
* [App Studio documentation GitLab repository](https://gitlab.cee.redhat.com/red-hat-trusted-application-pipeline/red-hat-trusted-application-pipeline)
<!-- * [Email: Stonesoup Development Team](mailto:Stonesoup@googlegroups.com) -->
<!-- * [Google chat: Stonesoup Users](https://groups.google.com/g/Stonesoup) -->

## Notes

This README file follows the content and syntax conventions defined in the
Systems Design and Engineering Continuous Integration Git Repository README
File Guide (The Source):
- https://source.redhat.com/groups/public/systems-design-and-engineering/continuousintegration/continuous_integration_wiki/xci_git_repository_readme_file


## References for documentation team

* We used AsciiDoc to document App Studio (https://docs.asciidoctor.org/asciidoc/latest/#about-asciidoc).
* We created this website using Antora (https://docs.antora.org/antora/latest/). We use Antora because it provides a search capability that we can customize.
* We manage documentation in GitLab. They are in a repository (<https://gitlab.cee.redhat.com/red-hat-trusted-application-pipeline/red-hat-trusted-application-pipeline>). We use GitLab to manage publication - continuous integration settings in the repository automatically generate the web site when changes are merged and GitLab Pages is used to publish the website here <https://red-hat-stone-soup.pages.redhat.com/stonesoup-documentation/>.

### Required tools

A set of tools is required to render the documentation from Antora/AsciiDoc to HTML, and they need to be installed on the local machine:
 * [NodeJS](https://nodejs.org/), install the latest LTS version
 * [Golang](https://go.dev/), install the latest version
 * [Git](https://git-scm.com/), install the latest version

To install on Fedora Linux run the following command:

```shell
$ sudo dnf install nodejs golang git-core
```

### Rendering the documentation

To render the documentation to HTML format run `npm run build`, this will output the rendered HTML files in the `public` subdirectory which can be opened in the browser.

For convenience there is also the `dev` script, that can be run with `npm run dev` to render and start a HTTP server at [http://localhost:8080](http://localhost:8080).

## Jira workflow

1. Open Epics based on the doc plan.
2. Outline sprint/milestone.

- Follow up with SMEs to confirm their availability.

3. Break Epics down into tasks.

4. Discuss and assign tasks.

- **New:** on your queue but you haven’t started yet.

- **Refinement:** research it, read up on it, talk to SMEs about it. In a Jira comment, you can recap your research and SME conversations. You understand it enough to make a GDoc or Merge Request (MR).
- For bigger doc tasks, like creating entirely new documents, writing abstracts, developing procedures, etc., you might find it best to start  in a GDoc.
- In the GDoc, you can receive reviews quickly and address reviews quickly. Once the doc is in good shape, you can take the content from the GDoc, and put in an ascii doc file and make a MR. This way, the MR is opened and closed quicker.
-  **In Progress:** you’re now writing or making a file update. You have something to share beyond a Jira comment or status update.
- **Review:** you’ve elicited a peer review from docs, devs, and QE. You address the review as it comes. During the review stage, your content can be in either a GDoc or MR.
- Depending on the task, you might not need a review from all three: dev, doc, QE. For instance, fixing a broken link might only require a QE review. Changing a grammatical error might only require a doc review. Use your best judgment.
- **Closed:** reviews are complete and addressed. The MR is merged and the content is published.

## Docs workflow with Dev and QE

1. Sprint planning.

- Does Docs have the bandwidth for this task?

- Will SMEs and QE be available to support Docs with this task for this sprint?

2. Research.

- Talke with SMEs. Gather information.

3. Review.

- If in a GDoc, add comments and update the GDoc until the content is ready to be converted into an ascii doc and shared in a MR.
- When the MR is created, the engineers review it and provide:
- Technical accuracy of content, not grammatical and language review.
- Provide user perspective.
- Writer responds to the review. Updates the Gdoc or MR and repeats until the review is complete and the doc is ready be published.

## Git workflow

### Forking and cloning Git Lab repository

1. Fork the git lab repository from the git lab user interface  (UI).
2. On the command line interface (CLI) on your local machine, run the following commands:
3. `git clone git@gitlab.com<your-gitlab-username>/<gitlab repository you’re cloning>`
4. `cd <gitlab repository>`
5. `git remote add -f upstream <git@gitlab.com>/<gitlab repository>`
6. `git checkout main`
7. `git remote -v`

- Run this command to confirm that you have origin and upstream configured.

8. Now you’re ready to start contributing!


### Making a merge request (MR)

1. `cd <name of place where you stored the cloned repo/<name of repo>`
    Ex: cd documents/Stonesoup-documentation/
2. `git checkout main`
3. `git fetch upstream`
    Git data from upstream repo (the main repo)
4. `git merge upstream/main`
    Update what’s on my local repo (my cloned repo, on my machine)
5. `git push`

- To make sure your fork is now up to date with your local copy

- You could say “git push origin” but it’s superfluous because it’s always origin :)
- Now everything is up to date (main, fork, clone)

6. `git checkout -b <feature-branch>`

- Make the name of the feature branch the same name as the issue
- Ex: `git checkout -b Stonesoup-170 upstream/main`

7. Make doc changes.

- Make the doc changes in your chosen editor: Atom, VS Code, etc.

8. Run antora to check and test your doc changes on a local host server

- There’s multiple ways to build docs locally with Antora, we’ll need to determine a way

9. `git status`

- Verifies that the files you made changes to have been registered as a changed file, and therefore, can be committed.

10. `git add .`

- `.` is a terminal thing.

- `.` means THIS directory. So it means add files from this current directory you’re on
- `git add` you’re adding stuff to git stage.

- You could actually list the doc instead of the `.` the `.` is easy because it adds EVERYTHING that has been changed. So you can add like 3 files to one commit. If no `.`, then you have to manually add each file!

11. `git status`

- Double check that your file is in fact staged to be committed.

- Your file(s) will be highlighted green in the CLI once they’ve been added. If it’s not highlighted green, it was not added to be committed :)

12. `git commit -m <name of commit message>`

- Simply ready to be pushed.

- Ex: `git commit -m Stonesoup-170 restructured procedure steps`

13. `git push -u origin <feature branch>`

- This command creates the MR, and the MR is asking to merge your feature branch into the main repository.

- You don’t need `git push -upstream origin <feature branch>` remember, origin is the default. Like in step 
5, it’s superfluous. You’re already on feature branch and staged the commit, so simply push it!

14. Go to GL to make the MR

15. Tag people, write messages, do what you must to receive peer reviews of your newly created MR.


### Making commits for a MR

1. `cd <location of repo>/<name of repo>`
2. `git checkout main`
3. `git fetch upstream`
4. `git merge upstream/main`

5. `git push`

- To make clone and fork up-to-date with master

6. `git checkout <feature-branch>`

7. `git pull --ff-only`

- These command makes sure your feature branch (always on your fork) is nync with the master repo (upstream), hence why we merge to main

8. Make doc changes

9. Run antora to check and test your doc changes on a local host server

10. `git status`

11. `git add . `

12. `git status`

- Double check that your file is in fact staged to be committed.

- Your file(s) will be highlighted green in the CLI once they’ve been added. If it’s not highlighted green, it was not added to be committed :)

13. `git commit --amend`

- This will add any updates to your previous commit within the MR. If you do want to create a 2nd commit in the MR, run the command: `git commit -m <name of commit message>`

14. `git push`

- After you make a MR, you ought to be able to simply run `git push` to make a new commit. If you get any error messages, try `git push -u origin <feature branch>`

15. Go to MR to ensure the commit has been made.

- Tag reviewers, direct their attention to specific areas of content or whatever you see fit.





### To generate output

* On your system: After setup (to set up follow reference information) run the following command on your terminal: `npx antora --fetch antora-playbook.yml`

* Merge you changes and refresh the App Studio documentation link, which is, <https://redhat-appstudio.github.io/docs.appstudio.io/Documentation/main>

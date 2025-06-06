# MDN Web Docs contribution guide

Thanks for taking the time to contribute to [MDN Web Docs][]! :tada:

This document covers project setup steps along with a set of guidelines for contributing to MDN Web Docs content.
Everyone participating in this project is expected to follow our [Code of Conduct](https://github.com/mdn/content/blob/main/CODE_OF_CONDUCT.md), which means adhering to [Mozilla's Community Participation Guidelines](https://www.mozilla.org/en-US/about/governance/policies/participation/).
If you want to jump right in, see [Getting started with MDN Web Docs][] for an overview of how to join, and the [Community resources][] on MDN.

## Getting started

Before contributing, make sure you're familiar with the project guidelines and conventions:

- [Writing guidelines][] - This page covers everything from how and what we write to general project guidelines.
- [Writing style guide][] - This covers the language and style we use and how we write and format code examples.
- [How to write in Markdown][] - This covers the Markdown features we support on MDN and custom extensions we've added.

### Prerequisite knowledge

We expect contributors to MDN to have some knowledge of web technologies before working on content.
We've put together relevant resources to get up to speed on specific topics before contributing:

- **Open source:** If you're new to open source projects, see the [Open source etiquette][] page.
- **Git and GitHub:** If you are unfamiliar with these, see the section [What do I need to get started?][] to get pointers on where to start.
- **Web technologies:** HTML, CSS, JavaScript, and more are covered in our [Learn web development][] tutorials.
- **MDN repositories:** To find out where everything lives in various MDN repositories, see our [MDN Web Docs repositories][] page.

### Documentation conventions

There are a few things to keep in mind about content on MDN and how it is maintained:

- A document's content is written in an `index.md` file.
- A document's `index.md` starts with "front-matter" described in [Front-matter](#front-matter).
- Documents have corresponding folders (the JavaScript page's `index.md` is in [`files/en-us/web/javascript`](files/en-us/web/javascript), for example).
- Document folders may contain images referenced by the `index.md` file in that folder.
- A document folder may contain child folders with child documents (e.g., [`files/en-us/web/javascript/reference/index.md`](files/en-us/web/javascript/reference/index.md)).
- Redirects are specified in [`_redirects.txt`](files/en-us/_redirects.txt).
  Do not edit this file manually! See [Moving documents](#moving-documents) for details.

#### Front matter

Each document's `index.md` starts with front-matter, which is written in [YAML](https://en.wikipedia.org/wiki/YAML).
The YAML is read by the MDN build system and is used to read the metadata of a document.

The front-matter must be the first thing in the file and must take the form of valid YAML set between triple-dashed lines (`---`).
Front-matter defines the document's `title` and `slug`, and may also include `status`, `browser-compat` and specification information.
Here's an example of front-matter from the [JavaScript page](files/en-us/web/javascript/index.md):

```yaml
---
title: JavaScript
slug: Web/JavaScript
---
```

### Setting up git and GitHub

You'll need [a GitHub account](https://github.com/join) to contribute to MDN Web Docs.
If you are comfortable working with git and GitHub, you can skip ahead to [Contributing to MDN](#contributing-to-mdn).
If you've created a new GitHub account and want to know what to do next, you can choose one of the following ways to manage changes:

- [GitHub UI](https://docs.github.com/en/repositories/working-with-files/managing-files) -
  This is the easiest way to contribute **small changes** described in [Simple changes](#simple-changes).
- [GitHub Desktop](https://docs.github.com/en/get-started/using-github/github-desktop) - A desktop app for managing interaction with GitHub.
- [GitHub CLI](https://docs.github.com/en/github-cli/github-cli/about-github-cli) - A command-line wrapper for interacting with GitHub.
- [`git`](https://git-scm.com/downloads) - You can use `git` from the command line to interact with GitHub.
  The examples in this document assume you are using this method.
  The [`git` cheat sheet](https://training.github.com/) and [Using Git](https://docs.github.com/en/get-started) guide are useful resources for beginners and advanced users.

### Simple changes

If you want to make a small change like fixing a typo, the GitHub UI is the easiest way to get started.
If you've found a typo on the [JavaScript landing page][], for example, you can propose a fix as follows:

1. Sign in to [GitHub](https://github.com/)
2. Navigate to [https://github.com/mdn/content](https://github.com/mdn/content)
3. Find the source file, in this case `files/en-us/web/javascript/index.md`
4. Click the edit (pencil) button

From there, the GitHub UI will walk you through the rest by creating a [fork](https://docs.github.com/en/get-started/quickstart/fork-a-repo) and a branch to commit your changes to.
After you have made changes to your branch, open a [pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) with your changes to be incorporated.

A pull request represents the work you want to be reviewed, approved, and merged into the `main` branch of the MDN repository.
See the [Creating a pull request](#creating-a-pull-request) for more details on creating and handling pull requests successfully.

If you're not certain of the changes that you want to make, [get in touch with us]!

> [!NOTE]
> You can click the **View the source on GitHub** link at the bottom of an MDN page to jump directly to the page source on GitHub.

### Forking and cloning the repository

If you want to make changes to more than one file, the GitHub UI is not very efficient because you have to make separate pull requests for each file you want to change.
Instead of using the GitHub UI, you need to use `git` or a client like the [GitHub Desktop](https://docs.github.com/en/get-started/using-github/github-desktop) or [GitHub CLI](https://docs.github.com/en/github-cli/github-cli/about-github-cli).
The following examples are using plain `git` commands, but you can use any of the clients mentioned above to perform the equivalent actions.

To fork and clone the repository:

1. [Create a fork](https://docs.github.com/en/get-started/quickstart/fork-a-repo) of the `mdn/content` repository to freely experiment with branches and changes.
   Assuming your GitHub username is `octocat`, your fork would be a copy of the `mdn/content` repository in your account at `https://github.com/octocat/content`.

2. Clone your fork to your local machine.
   Assuming your GitHub username is `octocat`, you would do something like this:

   ```bash
   # starting in a directory of your choice
   cd ~/repos
   # clone your fork of the repository
   git clone git@github.com:octocat/content.git
   ```

3. [Create a `remote`](https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes) to keep your clone and fork (`https://github.com/octocat/content`) up-to-date.
   This example adds a remote named `upstream`, but you can name it `mdn` or any other name you like.

   ```bash
   # starting in your clone directory
   cd ~/repos/content
   git remote add upstream git@github.com:mdn/content.git
   ```

   When you run `git remote -v`, you'll see that you have two remotes: `upstream` and `origin`.
   The `origin` remote is your fork (`https://github.com/octocat/content`) and the `upstream` remote is the `mdn/content` repository.

4. Keep your fork up-to-date often.
   You can do this by fetching the latest changes from the `mdn/content` repository and merging them into your fork.

   ```bash
   cd ~/repos/content
   # checkout your local clone's main branch
   git checkout main
   git fetch upstream
   # merge the latest content from the main branch of the mdn repository
   git merge upstream/main
   ```

5. Create a branch for your changes.
   This example creates a branch named `fix-typo`:

   ```bash
   cd ~/repos/content
   # checkout your local clone's main branch
   git checkout main
   # create a new branch named fix-typo
   git checkout -b fix-typo
   ```

## Contributing to MDN

The previous sections describe how to get started using the GitHub UI to make small changes to a single file and how to create a fork and clone the repository to prepare for making larger changes.
This section describes how to build the project locally and how to prepare your changes for submission.

### Preparing the project

To serve the site locally, you need to have [Node.js](https://nodejs.org/) and [Yarn 1 (Classic)](https://classic.yarnpkg.com/) installed.
You can check if these are installed by running the following commands:

```bash
node -v
yarn -v
```

After you have installed Node.js and Yarn, you can install the dependencies using `yarn`:

```bash
# Assuming your fork is in ~/repos/content
cd ~/repos/content
yarn
```

### Running the project

After you have installed all dependencies, you can start the local preview using `yarn start`:

```bash
yarn start
```

Once started, a live preview is available at `http://localhost:5042/`

Set your preferred editor by adding `EDITOR=...` into a `.env` file in the project root.
To specify VS Code as your preferred editor, for example, use the following command:

```bash
echo 'EDITOR=code' >> .env
```

You can set the `EDITOR` environment variable to any editor you like.
When browsing a page server locally, you can press **Open in your editor** to edit the current file in your preferred editor.

### Editing files and tracking changes in git

To edit files and track your changes, you should use feature branches.
Feature branches are created from the `main` branch and should be named after the feature you're working on.
This will make it easier to submit a pull request for your changes.

> [!NOTE]
> Open a discussion if your changes will contain large, complex or structural changes. Ask for feedback before embarking on large tasks.

1. When the server is running, make the changes you would like to make to one or more `index.md` files.

2. Open a browser and navigate to the equivalent pages you've changed.
   If you changed `files/en-us/web/javascript/index.md`, you would navigate to `http://localhost:5042/en-us/docs/web/javascript` in your browser, for example.

3. Check for detected flaws at the top of the previewed page. Some flaws may be automatically fixable.

4. Commit your changes to the branch (our example is using the `fix-typo` branch) and push the changes to your fork's remote:

   ```bash
   # Adding all files to the commit
   git add .
   # Making a commit with a message describing the changes
   git commit -m "Fix typo"
   # Pushing the commit to your fork
   git push
   # or "git push --set-upstream origin fix-typo" if you haven't pushed this branch before
   ```

#### Linting edited files

To ensure that all MDN documents follow the same formatting, we use both [Prettier](https://prettier.io/) and [MarkdownLint](https://github.com/DavidAnson/markdownlint) to format and lint Markdown files. This helps us enforce uniform styling across all documents with minimal reviewer intervention.

If you have a [local checkout](#forking-and-cloning-the-repository) of the repository and have [installed the dependencies](#preparing-the-project), or you are using [github.dev](https://github.dev/), a pre-commit hook will be installed which automatically runs while making a commit. To save some headache and improve your work flow while authoring, you may wish to [configure your editor to automatically run Prettier](https://prettier.io/docs/editors.html). Alternatively, you may run `yarn fix:md` in the command line to manually format all Markdown files.

> [!NOTE]
> Automatically formatting changes does not work for pull requests opened using the GitHub Web UI as described in the ["Simple changes" section](#simple-changes).
> This may result in failed status checks on pull requests. If you're not sure about how to fix this, [get in touch with us][] for help.

### Adding a new document

Adding a new document is relatively straightforward, especially if you can start by copying the `index.md` of a similar document.
There are a few things to keep in mind:

- Documents must be written in Markdown.
- A document is represented by an `index.md` file.
- If you're creating a new CSS document for a property called `foo`, create a new folder `files/en-us/web/css/foo/` and put the Markdown file in this folder (`files/en-us/web/css/foo/index.md`).
- A document's `index.md` file must start with front-matter that defines the `title`, `slug`, and, most of the time, `page-type`.
  You might find it helpful to refer to the front-matter within a similar document's `index.md`.

### Moving documents

Moving one or more documents (or an entire tree of documents) is made easier with the `yarn content move` command.
This command moves the file and fixes up redirects automatically. You can use this command as shown below:

```bash
yarn content move <from-slug> <to-slug> [locale]
```

> [!WARNING]
> Don't edit the `_redirects.txt` file manually.
> See the [Redirecting a document](#redirecting-a-document) section for more information.

To use `yarn content move`, provide the slug of the document you'd like to move (e.g., `Learn/Accessibility`), and the slug of its new location (e.g., `Learn/A11y`).
The locale of the existing document can be provided as an optional third argument (this defaults to `en-US`). For other locales,
`CONTENT_TRANSLATED_ROOT` has to be set correctly in your environment.
If the document you'd like to move contains child documents (i.e., it represents a document tree), the `yarn content move` command will move the entire tree.

Let's say you want to move the entire `/en-US/Learn/Accessibility` tree to `/en-US/Learn/A11y`, you can do so as follows:

1. Starting from a fresh branch:

   ```bash
   cd ~/repos/content
   # Fetch the latest changes from the main branch on mdn/content
   git fetch upstream
   git checkout main
   git merge upstream/main
   # create a new branch for your work
   git checkout -b moving-a11y
   ```

2. Move files with `yarn content move`.
   This will delete and modify existing files, as well as create new files.

   ```bash
   yarn content move Learn/Accessibility Learn/A11y
   ```

3. Once files are moved we need to update references to those files in the other content files as well. Use following command to update all the references automatically in one go:

   ```bash
   node scripts/update-moved-file-links.js
   ```

4. Commit all the changes and push your branch to the remote:

   ```bash
   git add .
   git commit -m "Move Learn/Accessibility to Learn/A11y"
   git push
   # or git push --set-upstream origin moving-a11y
   ```

### Deleting a document

Similar to moving files, you can delete documents or a tree of documents easily by using the `yarn content delete` command.

> [!WARNING]
> Don't delete files or directories from the repository manually; the `yarn content delete` command handles the necessary changes such as updating the `_wikihistory.json` file.

You can use this command as shown below:

```bash
yarn content delete <document-slug> [locale] --redirect <redirect-slug-or-url>
```

To use `yarn content delete`, provide the slug of the document you'd like to delete (e.g., `Learn/Accessibility`), and the locale as an optional second argument (this defaults to `en-US`).
If the slug of the page you wish to delete contains special characters, include it in quotes. For example:

```bash
yarn content delete "Glossary/Round_Trip_Time_(RTT)" --redirect Glossary/Latency
```

If the document has child documents (i.e., the document represents a document tree), you must specify the `-r, --recursive` option, else the command will fail.
Say you want to delete the entire `/en-US/Learn/Accessibility` tree and redirect all the deleted documents to `Web/Accessibility`. You can perform the following steps:

1. Start from a fresh branch.

   ```bash
   cd ~/repos/content
   # Fetch the latest changes from the main branch on mdn/content
   git fetch upstream
   git checkout main
   git merge upstream/main
   # create a new branch for your work
   git checkout -b deleting-a11y
   ```

2. Run the `yarn content delete` command and redirect all deleted documents.

   ```bash
   yarn content delete Learn/Accessibility --recursive --redirect Web/Accessibility
   ```

   > [!WARNING]
   > You should always add a redirect when deleting documents. If there is no obvious alternative, redirect to the nearest "parent" of the deleted topic.
   > If you forget to redirect when deleting a file, you can do it afterwards. See the [Redirecting a document](#redirecting-a-document) section.

3. Commit all of the changes and push your branch to the remote.

   ```bash
   git add .
   git commit -m "Delete Learn/Accessibility pages"
   git push
   # or git push --set-upstream origin moving-a11y
   ```

### Redirecting a document

If you are [moving a document](#moving-documents) as shown above you don't need to create a redirect.
However, you may need to do so when fixing a broken link or after [deleting a document](#deleting-a-document) without the `--redirect` flag.

You may do this by using the `yarn content add-redirect` command.

1. Start a fresh branch to work in:

   ```bash
   cd ~/repos/content
   # Fetch the latest changes from the main branch on mdn/content
   git fetch upstream
   git checkout main
   git merge upstream/main
   # create a new branch for your work
   git checkout -b deleting-a11y
   ```

2. Add a redirect with `yarn content add-redirect`. The target page can be a page on MDN or an external URL:

   ```bash
   yarn content add-redirect /en-US/path/of/deleted/page /en-US/path/of/target/page
   ```

3. Commit all of the changed files and pushing your branch to your fork:

   ```bash
   git add .
   git commit -m "Adding redirect after deleting Learn/Accessibility pages"
   git push
   # or git push --set-upstream origin deleting-a11y
   ```

### Creating a pull request

Once you've made your changes and pushed them to a branch on your fork, you can [create a pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request) to propose your changes to the `mdn/content` repository.
Someone from the MDN team or the MDN Web Docs community will review your changes and provide feedback.

For details on what to do next, see the [pull request etiquette section](#pull-request-etiquette) to see how to handle pull requests and get your content merged successfully.

#### Pull request etiquette

This is the exciting part of contributing to MDN as you're almost done with the contribution process!
Here are some things to keep in mind at this point:

- Your pull request must be **reviewed and approved** before it's merged into the `main` branch.
- **You do not need to request a review**; one or more reviewers will be selected for you automatically.
- **It can be up to 48 hours** for merged pull requests to have their changes published to [MDN Web Docs][].

During reviews, you may be asked to answer questions about your work or to make changes to your suggested edits.
This is a common part of the process of making changes in open source projects.
There are some important rules of etiquette to remember that will help during the review stage.

1. **Check tests** that are run automatically for pull requests (see [.github/workflows](.github/workflows)).
   If one or more of these tests fail, you must fix them.
   Your pull request will not be approved and merged if there are failing tests.
   If you don't know how to resolve the underlying issue(s), you can ask for help.

2. **Resolve conflicts** if your pull request has merge conflicts with the `main` branch.
   This is usually done by merging the `main` branch into your feature branch (`git pull upstream main`), and then pushing the updated branch to your fork (`git push`).

3. **Group logical changes** in each pull request so that it contains a single change or a related set of changes.
   If a pull request becomes too large or contains too many unrelated changes, a reviewer may close your pull request and ask you to submit a new pull request for each set of changes.

4. **Don't re-open pull requests** closed by a reviewer.

5. **Don't use `git rebase`** of `main` over your branch.
   Your changes are replayed on top of the current main branch at that point in time.
   This might confuse reviewers as notifications on GitHub lead to nowhere.

## License

When contributing to the content you agree to license your contributions
according to [our license](LICENSE.md).

<!---
Reference links syntax is used here because of linting markdown files ("fqdn-moz-links" rule).
See https://github.com/mdn/content/pull/21432 and https://github.com/mdn/content/pull/38369.
It can be replaced with the normal links syntax after successfully closing https://github.com/DavidAnson/markdownlint/issues/673.
-->

[mdn web docs]: https://developer.mozilla.org/
[getting started with mdn web docs]: https://developer.mozilla.org/en-US/docs/MDN/Community/Getting_started
[community resources]: https://developer.mozilla.org/en-US/docs/MDN/Community
[writing guidelines]: https://developer.mozilla.org/en-US/docs/MDN/Writing_guidelines
[writing style guide]: https://developer.mozilla.org/en-US/docs/MDN/Writing_guidelines/Writing_style_guide
[how to write in markdown]: https://developer.mozilla.org/en-US/docs/MDN/Writing_guidelines/Howto/Markdown_in_MDN
[open source etiquette]: https://developer.mozilla.org/en-US/docs/MDN/Community/Open_source_etiquette
[what do i need to get started?]: https://developer.mozilla.org/en-US/docs/MDN/Community/Getting_started#what_do_i_need_to_get_started
[learn web development]: https://developer.mozilla.org/en-US/docs/Learn_web_development
[mdn web docs repositories]: https://developer.mozilla.org/en-US/docs/MDN/Community/Our_repositories
[javaScript landing page]: https://developer.mozilla.org/en-US/docs/Web/JavaScript
[get in touch with us]: https://developer.mozilla.org/en-US/docs/MDN/Community/Communication_channels

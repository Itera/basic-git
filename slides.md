---
theme: default
class: 'text-center'
highlighter: shiki
lineNumbers: true
drawings:
  persist: false
css: unocss
---

# Basic Git Course

<span class="abs-b m-6">
Itera
</span>


---
layout: center
---

# What Is Git?

<v-clicks>

- Distributed version control system
- Software developers are the target audience
  - Manage different versions of source-code
  - Work on the same source-code in parallel
- De-facto standard in the industry

</v-clicks>


---
layout: center
---

# How Does It Work?

<v-clicks>

- Stores a history of changes to your source-code
  - Which lines have been added?
  - Which lines have been removed?
- Each developer works on their local copy of the source-code
  - Controls when their changes is uploaded (for sharing)
  - Controls when other's changes is downloaded
  - Eventual conflicts must be manually resolved

</v-clicks>


---
layout: two-cols
---

# Basic Vocabulary

<v-clicks>

- **Tracked files**
  - files that are version controlled by git
- **Staging/Index**
  - changes prepared for commit
- **Commit**
  - an atomic unit of changes to the source-code
  - <u>connected</u> to its `parent`(s), or predecessor(s)
  - has a _hash_ that uniquely identifies it
- **Tag**
  - pointer to a specific `commit`, with a friendly name

</v-clicks>

::right::

# &nbsp;

<v-clicks>

- **Branch**
  - a <u>connected</u> graph of `commit`s
  - can `merge` in another `branch` to include its `commit`s
  - can be `upload`ed by `push`ing it to a `remote`
- **Remote**
  - a repository of `branch`es and their `commit`s
  - e.g. a GitHub repository
- **Pull request**
  - a request to `merge` one branch into another
  - contains a summary of changes that can be reviewed

</v-clicks>

<style>
  ul {
    font-size: 1rem;
  }
</style>


---
layout: center
---

# Basic Commands


---
layout: center
---

# Basic Commands - Managing Changes

<v-clicks>

- `git status`
  - show a list of changed files
- `git add`
  - add changes to _staging_
- `git reset`
  - removes changes from _staging_
- `git commit`
  - saves changes in _staging_ as a commit
- `git log`
  - show commits in current branch
- `git stash`
  - temporary undo _tracked_ changes

</v-clicks>


---
layout: center
---

# Basic Commands - Communicating With Remote

<v-clicks>

- `git clone`
  - downloads source-code from remote
- `git push`
  - pushes branch to remote
- `git pull`
  - merges in commits from remote

</v-clicks>


---
layout: center
---

# Basic Commands - Managing Pointers

<v-clicks>

- `git tag`
  - creates a new tag
- `git branch`
  - creates a new branch
- `git switch`
  - switches to branch
- `git merge`
  - merges in commits from branch

</v-clicks>


---
layout: center
---

# Conventional Workflow

<v-clicks>

- Everone agrees on a shared "trunk" branch
  - E.g. `main` or `master`
- Each person works in their own branches off the "trunk"
  - Each branch is scoped to a set of related changes
- Pull requests are created for "completed" branches
  - Merges to "trunk" are disallowed without peer approval

</v-clicks>


---
layout: center
---

# Branching Strategy

How teammates cooperate


---
layout: center
---

# Branching Strategy - Vocabulary

<v-clicks>

- **Long-living branches**
  - Shared ownership
  - Never deleted
  - Example: the "trunk" branch
- **Short-lived branches**
  - Usually owned by a single person
  - Offshoots of long-living branches
  - Ideally deleted upon completion
    - E.g. after merged into the "trunk" branch

</v-clicks>


---
layout: center
---

# Branching Strategy - GitHub Flow

<v-clicks>

- A single long-living branch, the trunk
  - E.g. `main`
- Changes to the trunk comes through PRs
  - Created from short-lived branches
  - Should have descriptive names
- Changes to the trunk is deployed immediately
  - I.e. it should contain working code

</v-clicks>


---
layout: center
---

# Branching Strategy - Git Flow

<v-clicks>
<ul>
  <li>
    Two long-living branches
    <ul>
      <li><code>main</code>: contains production code</li>
      <li><code>develop</code>: works like "the trunk"</li>
    </ul>
  </li>
  <li>Three types of short-lived branches
    <table class="text-xs">
      <tr>
        <th>Name</th>
        <th>Offshoot off</th>
        <th>Merged into</th>
        <th>Purpose</th>
      </tr>
      <tr>
        <td><code>feature</code></td>
        <td><code>develop</code></td>
        <td><code>develop</code></td>
        <td>New features</td>
      </tr>
      <tr>
        <td><code>release</code></td>
        <td><code>develop</code></td>
        <td><code>main</code>, <code>develop</code></td>
        <td>Prepares "trunk" for deploy</td>
      </tr>
      <tr>
        <td><code>hotfix</code></td>
        <td><code>main</code></td>
        <td><code>main</code>, <code>develop</code></td>
        <td>Quick patches to production</td>
      </tr>
    </table>
  </li>
  <li>Pull requests may be used to merge branches</li>
  <li>Tags are created to manage release versions</li>
</ul>
</v-clicks>


---
layout: center
---

# Branching Strategy - Discussion

<ul>
  <li v-click="1">Git Flow is very complex
    <ul>
      <li v-click="2">Splits the team</li>
      <li v-click="3">Difficult to keep branches in sync</li>
      <li v-click="4">A lot of merge conflicts</li>
      <li v-click="5">More control over different versions</li>
    </ul>
  </li>
  <li v-click="6">GitHub Flow was created as a response
    <ul>
      <li v-click="7">More in line with agile methods</li>
      <li v-click="8">Short path to production</li>
      <li v-click="9">"Go fast and break things"</li>
    </ul>
  </li>
</ul>


---
layout: center
---

# Naming Convention

<ul>
  <li v-click="1">Branch names
    <ul>
      <li v-click="1">Format: <code>&lt;branch-type&gt;/&lt;descriptive-name&gt;</code>
        <ul>
          <li v-click="2">e.g. <code>feature/chatbot</code></li>
        </ul>
      </li>
      <li v-click="3">Typical "branch types":
        <ul>
          <li><code>bugfix</code>, <code>refactor</code>, <code>test</code>, <code>style</code>, and <code>chore</code></li>
        </ul>
      </li>
    </ul>
  </li>
  <li v-click="4">Commit message
    <ul>
      <li v-click="5">
        Imperative form
        <ul>
          <li>E.g. "Add chatbot", not "Added chatbot"</li>
        </ul>
      </li>
      <li v-click="6">First line should not exceed 60 characters</li>
      <li v-click="8">"Standard" proposed by <a href="https://www.conventionalcommits.org/">Conventional Commits</a></li>
    </ul>
  </li>
</ul>


---
layout: center
---

# Pull Requests

It's time for peer reviews!


---
layout: center
---

# Great Things About PRs

<v-clicks>

- Learning experience
  - Input from peers
  - Seeing your peers solutions
- Catching unnecessary errors early
  - Easy to tunnel vision when you're alone
  - Ensures a higher level of quality
- Shared ownership
  - At least two people knows every piece of code
  - Everyone is responsible failures

</v-clicks>


---
layout: center
---

# How To Review PRs

<ul>
  <li v-click="1">Be nice
    <ul>
      <li v-click="2">People shouldn't feel attacked</li>
    </ul>
  </li>
  <li v-click="3">Wording is key
    <ul>
      <li v-click="4">Use "we" instead of "you"</li>
      <li v-click="5">Prefer suggestions over confrontations</li>
      <li v-click="6">Don't: "You need to do this"</li>
      <li v-click="7">Do: "I think we should do this instead"</li>
    </ul>
  </li>
  <li v-click="8">Include context in your comments
    <ul>
      <li v-click="9">Not everyone thinks alike</li>
      <li v-click="10">Don't: "This is doesn't work, do this instead"</li>
      <li v-click="11">Do: "This doesn't work when [...], try this instead"</li>
    </ul>
  </li>
</ul>


---
layout: center
---

# When Creating PRs...

<v-clicks>

- Make it easy for reviewers
  - Break big changes into smaller commits
  - Include screenshots of UI changes
  - Less overhead means more feedback!
- Link PRs relevant _tasks_
  - E.g. JIRA issues or DevOps work items
  - Tracks progress and records a history
  - Handy for communicating with non-developers

</v-clicks>


---
layout: center
---

# Beyond Basics


---
layout: center
---

# Beyond Basics - Rewrite History

<v-clicks>

- `git commit --amend`
  - save changes to previous commit
- `git commit --fixup`
  - creates a commit marked as fixing another commit
  - relvant commits can be squashed together using rebase
- `git rebase`
  - changes the parent of a commit
  - can also edit, squash, and reword commits
- `git push --force-with-lease`
  - override history in remote only if you are up-to-date
- **<span class="text-red-400">Important</span>**: be careful when rewriting history
  - Avoid rewriting commits pushed to remote

</v-clicks>


---
layout: center
---

# Beyond Basics - Fine Control

<v-clicks>

- `git add --patch`
  - only add some changes from files to staging
- `git fetch`
  - get but don't merge in updates from remote
- `git restore`
  - restore the previous state of a file
- `git revert`
  - undo changes made by a commit
- `git cherry-pick`
  - copy commits onto the current branch

</v-clicks>


---
layout: center
---

# Beyond Basics - Handy Tools

<v-clicks>

- `git bisect`
  - binary search through commits
- `git reflog`
  - show full history of commands
  - includes "forgotten" commits
- `git worktree`
  - check out branch without switching branch

</v-clicks>


---
layout: center
---

# Beyond Basics - Configuration

- Default editor
- Three-way merge
- Auto-squashing
- SSH keys


---
layout: center
---

# Learning Materials & Tools

- [gittutorial](https://git-scm.com/docs/gittutorial)
- [Itera Git Fagkveld](https://github.com/Itera/git-fagkveld)
- [Learn Git Branching](https://learngitbranching.js.org/)
- [Git excercises](https://gitexercises.fracz.com/)


---
layout: center
---

# Questions?
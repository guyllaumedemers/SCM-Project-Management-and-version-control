# Software configuration management, Introduction to project management and version control

### Using a version control system and why it matters.

**Wikipedia** : "Version control is a component of software configuration management. As a developer edits code, the version control system takes a snapshot of the files. It then saves that snapshot permanently so it can be recalled later if needed."

#### Project

Example details are grouped into subject related points and showcase investigation result on the subject of software configuration management and version control. Further details will be provided on more advance features that are covered in the making of our examples.

#### What this README.md is not

Be aware that some of the tooling used in the making of this `Demo` project won't be covered here. External documentations will be provided for your own benefit, which in most case, are also where most of the information mentioned here will be coming from.

## What's Software configuration management

**Wikipedia** : "Software configuration management is the task of tracking and controlling changes in the software, part of the larger cross-disciplinary field of configuration management. SCM practices include [revision control](https://en.wikipedia.org/wiki/Version_control) and the establishment of [baselines](https://en.wikipedia.org/wiki/Baseline_(configuration_management)). If something goes wrong, SCM can determine the "what, when, why and who" of the change."

#### Version control (or Revision control)

**Wikipedia** : "In computer software engineering, revision control is any kind of practice that tracks and provides control over changes to source code. Software developers sometimes use revision control software to maintain documentation and configuration files as well as source code."

* [Git](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F)
* [Helix Core](https://www.perforce.com/manuals/p4guide/Content/P4Guide/chapter.overview.html)
* [...](https://en.wikipedia.org/wiki/List_of_version-control_software)

# How does it works?

Revision control manages changes to a set of data over time. When data that is under revision control is modified, after being retrieved by checking out, this is not in general immediately reflected in the revision control system (in the repository), but must instead be checked in or committed.

# Types of version control systems

### Centralized

Traditional revision control systems use a centralized model where all the revision control functions take place on a shared server. If two developers try to change the same file at the same time, without some method of managing access the developers may end up overwriting each other's work. Centralized revision control systems solve this problem in one of two different source management models : [file locking](https://en.wikipedia.org/wiki/File_locking) and [version merging](https://en.wikipedia.org/wiki/Merge_(version_control)).

![centralized_vc](https://github.com/guyllaumedemers/SCM-Project-Management-and-version-control/blob/master/res/Centralized_vc.png)

### Distributed

Distributed version control systems (DVCS) use a peer-to-peer approach to version control, as opposed to the client–server approach of centralized systems. Distributed revision control synchronizes repositories by transferring patches from peer to peer. There is no single central version of the codebase; instead, each user has a working copy and the full change history.

![distributed_vc](https://github.com/guyllaumedemers/SCM-Project-Management-and-version-control/blob/master/res/Distributed_vc.png)

# How to setup a distributed system

### Git

Git is a fast, scalable, distributed revision control system with an unusually rich command set that provides both high-level operations and full access to internals.

## What you need to know

### File Versionning

The major difference between Git and any other VCS is the way Git thinks about its data. Conceptually, most other systems store information as a list of file-based changes. Git doesn’t think of or store its data this way. Instead, Git thinks of its data more like a series of snapshots of a miniature filesystem.

#### Delta

![delta-based](https://github.com/guyllaumedemers/SCM-Project-Management-and-version-control/blob/master/res/Deltas.png)

#### Snapshot

![snapshot](https://github.com/guyllaumedemers/SCM-Project-Management-and-version-control/blob/master/res/Snapshots.png)

**Tips** : "I strongly suggest you visit [Snapshots, Not Differences](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F) for futher details on how Git differ from other typical VCS. Also, in-depth explanation on how Git handle **blob**, **tree object** and **commit object**, which are key concept, can be found [here](https://git-scm.com/book/en/v2/Git-Internals-Git-Objects)."

### Understanding Git States

**Pay attention now** - Git has three main states that your files can reside in: **modified**, **staged**, and **committed**:

* **Modified** : means that you have changed the file but have not committed it to your version database yet.
* **Staged** : means that you have marked a modified file in its current version to go into your next commit snapshot.
* **Committed** : means that the data is safely stored in your local database.

![states](https://github.com/guyllaumedemers/SCM-Project-Management-and-version-control/blob/master/res/Git_states.png)

*See [What's Git](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F) to get a more in-depth understanding of Git Workflow!*

### Git CLI

##### Example - GitBash Cmd-line

```
//  Staging Modified/or Untracked file

C:> echo "HelloWorld" > HelloWorld.txt			(.txt - make sure it's encoded in utf-8)
C:> git status
C:> git add HelloWorld.txt
C:> git status
```

**Notes** : Our first `git status` will output to the console that our newly created .txt hasn't yet been tracked by git. Once stage via `git add`, the output console will display that the change is ready to be commited to our local workspace, not the remote. Remember that version tracking is done locally as you own a copy of the full file history from the initial `git clone` of the remote repository.

**Tips** : `git add .` act a as a wildcard, and stage all modified files, plus untracked files.

##### Example - GitBash Cmd-line

```
//  Commiting Staged file

C:> echo "HelloWorld" > HelloWorld.txt			(.txt - make sure it's encoded in utf-8)
C:> git add HelloWorld.txt
C:> git commit		(requires a 'commit' message)
C:> git status
```

**Tips** : `git commit -m "SomeMessage"` allow inlining the commit process.

##### Example - GitBash Cmd-line

```
//  Diffing Modified/or Staged file

C:> echo "HelloWorld_v1" > HelloWorld.txt		(.txt - make sure it's encoded in utf-8)
C:> git add HelloWorld.txt
C:> git commit -m "SomeMessage"
C:> echo "HelloWorld_v2" > HelloWorld.txt
C:> git diff
```

**Tips** : `git diff` will output to the console the delta on the modified file vs. the staged version. `git diff --staged` will output to the console the delta on the staged file vs. the commited version.
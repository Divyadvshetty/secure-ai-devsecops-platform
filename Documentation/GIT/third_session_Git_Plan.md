# Create Six Hour Git Plan

# Module 3: Source Code Management (SCM) with Git and GitHub
6 hours – Complete within prescribed duration
Beginner to Industry-ready
This module will be designed using your
Industry-Ready DevOps Training Program master prompt
.
The objective is not simply to teach students Git commands. By the end of these six hours, students should be able to independently manage source code, work with branches, resolve basic collaboration issues, and manage GitHub repositories like a junior DevOps engineer working in an actual company.
1. Six-hour training plan
I recommend dividing the module into
three sessions of two hours each
.
Session
Duration
Topics
Expected capability
1
2 hours
VCS fundamentals, Git architecture, installation, configuration, repositories, Git file workflow, important commands,
.gitignore
Independently manage local Git repositories
2
2 hours
Undoing changes, reset, revert, branching, merging, rebase, squash, stash, branching strategies
Manage code changes and collaborate safely
3
2 hours
GitHub introduction, remote repositories, push, pull, fetch, clone, upstream, practical collaboration
Work with remote repositories and GitHub
Total: 3 × 2 hours = exactly 6 hours
### How we will teach this module
Students will progressively build one practical project:
DevOps Training Application – Source Code Management
They will:
Create a local project.
Track changes using Git.
Commit different versions.
Create feature branches.
Merge changes.
Resolve a merge conflict.
Push the project to GitHub.
Work with remote repositories.
We will use a simulated company development workflow rather than isolated command demonstrations.
2. Session-wise learning objectives
## Session 1 – Git Fundamentals
2 hours
gitlearn.io
What is version control and why SCM exists.
Centralized vs Distributed Version Control Systems.
Git architecture and internal working.
Git installation and configuration.
Repository initialization and cloning.
Working directory, staging area and repository.
git status
,
add
,
commit
,
log
,
diff
.
.gitignore
and basic repository management.
## Session 2 – Git Branching and Advanced Operations
2 hours
youtube.com
Undoing changes: restore, reset and revert.
Git branching and branch management.
Merge and merge conflicts.
Rebase and squash.
Git stash.
Git Flow, trunk-based development and feature branching.
Safe troubleshooting and recovery.
## Session 3 – GitHub and Remote Repository Management
2 hours
southgreenplatform.github.io
GitHub introduction and its relationship with Git.
Creating repositories on GitHub.
Remote repository configuration.
git remote
,
push
,
pull
,
fetch
,
clone
.
Origin, upstream and tracking branches.
Collaboration workflow.
Final practical assignment.
## Session 1 – Git Fundamentals and Local Repository Management
2 hours
Beginner level
Hands-on
### A. Session information
Session title:
Understanding Version Control Systems and Working with Git
Duration:
120 minutes
### Learning objectives
By the end of this session, students should be able to:
Explain why version control systems are required.
Differentiate centralized and distributed version control.
Explain why Git is a distributed version control system.
Install and configure Git.
Create and manage local Git repositories.
Explain Git's working directory, staging area and commit history.
Execute fundamental Git commands.
Configure
.gitignore
.
Identify and troubleshoot common Git errors.
### Prerequisites:
Basic computer knowledge.
Basic familiarity with files and directories.
Basic terminal knowledge (Linux shell or Windows PowerShell).
### B. Time allocation
Time
Topic
Duration
00–15 min
Why version control exists
15 min
15–30 min
VCS types and Git architecture
15 min
30–45 min
Git installation and configuration
15 min
45–70 min
Creating repositories and Git workflow
25 min
70–90 min
Important Git commands
20 min
90–100 min
.gitignore
10 min
100–115 min
Hands-on lab and break/fix
15 min
115–120 min
Assessment and recap
5 min
Total
120 min
### C. Concept explanations – Trainer teaching notes
### Topic 1: What is Version Control?
Start with a question:
Imagine you are a software developer working on a banking application. You have developed a feature that calculates customer interest.
You save your file:
Plain text
interest-calculator.java
You make some changes and save it again.
A few days later:
Your new code has a bug.
The previous version was working.
You don't remember exactly what you changed.
Another developer has modified the same file.
Your team wants to know who introduced the bug.
How will you recover the previous working version?
This is the problem that Version Control Systems (VCS) solve.
Definition:
A Version Control System is a tool that records changes made to files over time so that you can track, compare, recover and collaborate on different versions of a project.
Real-life analogy:
Think about writing a book.
Version 1: First draft.
Version 2: Grammar corrections.
Version 3: New chapter added.
Version 4: Editor modifies some paragraphs.
Instead of maintaining four separate copies of the book, a version control system maintains a history of changes.
You can identify what changed, when it changed and who changed it.
Why do companies need VCS?
Business problem
How VCS helps
Developer accidentally deletes code
Recover previous versions
Multiple developers work together
Track and integrate changes
Production application breaks
Identify changes and roll back safely
Need to audit code changes
Identify author, time and commit history
New feature development
Work independently using branches
Security investigation
Trace changes to sensitive files
### Topic 2: Types of Version Control Systems
Explain that Git was not the first version control system.
There are two major architectural approaches students should understand.
1. Centralized Version Control System (CVCS)
janbasktraining.com
In centralized version control:
A central server maintains the repository.
Developers connect to the central server.
They check out files, make changes and commit changes.
The central server maintains the shared version history.
Examples:
Apache Subversion (SVN)
CVS (Concurrent Versions System)
Perforce Helix Core (centralized server-based workflow).
Real-world scenario:
Imagine five developers working on a banking application.
All five developers access the same central version control server.
If the central server becomes unavailable, developers may not be able to perform normal repository operations such as committing changes.
2. Distributed Version Control System (DVCS)
medium.com
In distributed version control:
Every developer can have a complete local repository.
The local repository contains project history.
Developers can commit changes locally.
They can exchange changes with other repositories.
A central remote repository can be used for team collaboration.
Examples:
Git
Mercurial
Important interview question:
Why is Git called a distributed version control system?
Answer: Because each cloned Git repository contains the project's history and can perform most version-control operations independently without requiring continuous connectivity to a central server.
Feature
Centralized VCS
Distributed VCS
Repository architecture
Central server
Multiple complete repositories
Local commits
Generally not supported in traditional CVCS workflows
Supported
Offline history operations
Limited
Supported
Examples
SVN, CVS
Git, Mercurial
Server dependency
Higher
Lower for local operations
### Topic 3: Git vs GitHub
This distinction is extremely important.
Many beginners think Git and GitHub are the same technology.
They are not.
Git
A distributed version control system that tracks changes in source code.
GitHub
A cloud-based platform for hosting Git repositories and collaborating on software projects.
Explain with an analogy:
Git is the mechanism that tracks changes in your documents.
GitHub is an online collaboration platform where your team can share those tracked documents.
Other Git hosting platforms include:
GitLab
Bitbucket
Azure Repos
Industry connection:
A DevOps engineer may use Git locally, GitHub for source code hosting, Jenkins for CI/CD and Kubernetes for application deployment. These are different tools performing different responsibilities.
Topic 4: How Git works internally
This is the most important technical concept of Session 1.
Explain that Git does not simply save multiple copies of a file. It maintains a database of objects representing the contents and structure of your project.
medium.com
Introduce these four components:
1. Working Directory
This is the actual project folder where developers create, edit and delete files.
Example:
Plain text
student-app/
├── README.md
├── app.py
└── requirements.txt
2. Staging Area (Index)
This is the preparation area where developers select which changes should be included in their next commit.
Analogy: Before sending a parcel, you select and pack the items you want to send.
You do not have to commit every modified file.
3. Local Repository
This stores committed project history and Git objects.
A commit represents a recorded state of the project.
4. HEAD
HEAD generally points to the currently checked-out branch, or directly to a commit in detached HEAD state.
For beginners, explain it as the reference indicating the current position in the Git history.
The Git file lifecycle
gist.github.com
Explain these states:
State
Meaning
Untracked
Git is not tracking the file yet
Unmodified
Tracked file has no new changes
Modified
Tracked file has been changed
Staged
Changes are selected for the next commit
Committed
Changes are recorded in repository history
Important internal concepts – introduce, don't deep-dive yet:
Git object
Responsibility
Blob
Stores file content
Tree
Represents directory structure and references blobs or other trees
Commit
Records a project snapshot and references a tree and parent commit(s)
Tag
Provides a named reference, often used for releases
Git uses content-based hashing (SHA-1 in traditional repositories; SHA-256 is also supported in newer repository formats) to identify objects.
A useful command to demonstrate:
Bash
git cat-file -t HEAD
Expected output:
Plain text
commit
This demonstrates that HEAD resolves to a commit object.
Do not spend time teaching Git object internals in depth today. Move the advanced object inspection to home practice.
D. Git installation and configuration
Step 1: Install Git
For Windows students:
Official download:
Git official downloads
.
Install Git for Windows.
The installer provides:
Git Bash.
Git command-line tools.
Git GUI.
Git integration with Windows.
For Ubuntu:
Bash
sudo apt update
sudo apt install git -y
For macOS:
Bash
brew install git
Step 2: Verify installation
Bash
git --version
Example:
Plain text
git version 2.x.x
The actual version will depend on the installed release.
Step 3: Configure Git identity
Bash
git config --global user.name
"Student Name"
git config --global user.email
"student@example.com"
Explain the options:
config
: Configure Git settings.
--global
: Apply settings to the current user's Git environment.
user.name
: Author name associated with commits.
user.email
: Author email associated with commits.
Verify:
Bash
git config --global --list
Expected output:
Plain text
user.name=Student Name
user.email=student@example.com
Trainer explanation:
Why is this required?
When Git creates a commit, it records author and committer information. Git does not automatically know the developer's identity.
Important: These settings are commit metadata, not authentication credentials for GitHub.
Other useful configuration commands
Bash
# Set the default initial branch name
git config --global init.defaultBranch main
# Set a default editor (example: VS Code)
git config --global core.editor
"code --wait"
# Display where a configuration value is defined
git config --show-origin --list
# Display all effective configuration
git config --list
Explain that Git configuration has different scopes:
System: Applies to all users on the machine.
Global: Applies to the current operating-system user.
Local: Applies to a particular repository.
Local repository configuration takes precedence over global and system configuration.
E. Creating and managing Git repositories
Step 1: Create a project directory
For Windows PowerShell or Git Bash:
Bash
mkdir devops-scm-lab
cd devops-scm-lab
Create sample files:
Bash
echo
"# DevOps Training Application"
>
README.md
echo
"print('Hello DevOps')"
>
app.py
Your directory:
Plain text
devops-scm-lab/
├── README.md
└── app.py
Step 2: Initialize a Git repository
Bash
git init
Expected output resembles:
Plain text
Initialized empty Git repository
Explain:
git
: Git command-line interface.
init
: Initializes a new repository in the current directory.
Git creates a hidden
.git
directory.
Bash
ls -la
For PowerShell:
powershell
Get-ChildItem -Force
Explain that
.git
stores repository metadata, objects, references and configuration.
Important:
Never manually modify
.git
internals unless you understand exactly what you are doing.
Step 3: Check repository status
Bash
git status
Expected output will identify:
Plain text
Untracked files:
README.md
app.py
Explain that files exist in the directory, but Git has not started tracking them.
Step 4: Stage files
Bash
git add README.md
This stages only the README file.
To stage all changes in the current directory:
Bash
git add
.
Explain the difference:
git add filename
: Stage a particular file.
git add .
: Stage new, modified and deleted changes under the current directory.
Verify:
Bash
git status
Expected output:
Plain text
Changes to be committed:
new file: README.md
Step 5: Commit changes
Bash
git commit -m
"Initial commit: Add README"
Explain:
commit
: Record staged changes in repository history.
-m
: Supply the commit message.
Expected output resembles:
Plain text
[main (root-commit) abc1234] Initial commit: Add README
1 file changed, 1 insertion(+)
The commit hash shown in actual output will differ.
Step 6: View commit history
Bash
git log
This displays:
Commit hash.
Author.
Date.
Commit message.
Useful variations:
Bash
git log --oneline
Compact commit history.
Bash
git log --oneline --graph --all
Visual representation of branches and commit history.
Bash
git show HEAD
Displays information and changes associated with the current commit.
F. Understanding the Git workflow through practical execution
This is where students should spend time executing commands themselves.
medium.com
Trainer demonstration:
Modify the application:
Bash
echo
"print('Version 2')"
>>
app.py
Check:
Bash
git status
Git identifies the file as modified.
View changes:
Bash
git diff
Expected output resembles:
Diff
+
print('Version 2')
Stage the file:
Bash
git add app.py
View staged changes:
Bash
git diff --staged
Commit:
Bash
git commit -m
"Add application version 2"
View history:
Bash
git log --oneline
Now students should understand:
Plain text
Developer modifies file
|
v
Working Directory
|
git add
|
v
Staging Area
|
git commit
|
v
Local Repository
Critical distinction:
git add
does not save a commit. It prepares selected changes for a future commit.
git commit
records the staged changes in local repository history.
G. Important Git commands – Session 1 cheat sheet
Command
Purpose
git --version
Check installed version
git config
Configure Git
git init
Initialize repository
git status
Check working tree
git add
Stage changes
git commit
Record changes
git log
View history
git diff
Compare unstaged changes
git diff --staged
Compare staged changes
git show
Inspect commit
git ls-files
List tracked files
git rev-parse --show-toplevel
Show repository root
git cat-file -t HEAD
Inspect Git object type
Other useful commands:
Bash
# Display current branch
git branch --show-current
# Display repository root
git rev-parse --show-toplevel
# List files tracked by Git
git ls-files
# Display the latest commit
git log
-
1
--oneline
# Display differences between two commits
git diff HEAD
~
1
HEAD
H. Understanding .gitignore
Explain the business problem first.
Imagine a Python application with the following directory:
Plain text
student-app/
├── app.py
├── README.md
├── .env
├── __pycache__/
├── venv/
└── logs/
Should all these files be uploaded to source control?
No.
Some files should not be committed:
Temporary files.
Python cache files.
Virtual environments.
Local configuration files.
Generated logs.
Build output.
Create
.gitignore
:
Bash
touch .gitignore
For Windows PowerShell:
powershell
New-Item
.
gitignore
-ItemType
File
Add:
gitignore
# Python cache
__pycache__/
*.pyc
# Virtual environment
venv/
.env/
# Environment configuration
.env
# Logs
*.log
logs/
# IDE
.vscode/
# OS files
.DS_Store
Thumbs.db
Explain the syntax:
Pattern
Meaning
*.log
Ignore files ending in
.log
__pycache__/
Ignore matching directories
.env
Ignore files named
.env
logs/
Ignore matching directories
!important.log
Negate a previous ignore pattern, subject to Git's parent-directory rules
Important industry scenario:
A developer accidentally commits an application's
.env
file containing database passwords.
Adding
.env
to
.gitignore
prevents future untracked
.env
files from being added automatically, but does not remove a file already tracked by Git.
To stop tracking a previously committed file while keeping the local copy:
Bash
git rm --cached .env
git commit -m
"Stop tracking environment file"
If a credential was exposed, simply removing the file is insufficient. Rotate the credential and follow the organization's incident response process. Git history may still contain the old secret.
I. Hands-on laboratory – Student practical
Mandatory practical
Lab title:
Create and manage your first Git repository.
Industry scenario:
You have joined a DevOps team maintaining an internal student management application. Your team lead asks you to create a Git repository, maintain source code history and ensure that temporary files and environment configurations are not committed.
Lab 1: Create the repository
Students execute:
Bash
mkdir student-management-app
cd student-management-app
git init
echo
"# Student Management Application"
>
README.md
echo
"print('Student Management System')"
>
app.py
git status
Expected outcome: Both files appear as untracked.
Lab 2: Commit the first version
Bash
git add
.
git status
git commit -m
"Initial commit: Create student application"
git log --oneline
Expected outcome: Students should see the first commit in history.
Lab 3: Introduce application changes
Bash
echo
"print('Application version 2')"
>>
app.py
git status
git diff
git add app.py
git diff --staged
git commit -m
"Update application version 2"
git log --oneline
Expected outcome: Two commits should be visible.
Lab 4: Configure .gitignore
Bash
echo
".env"
>>
.gitignore
echo
"*.log"
>>
.gitignore
echo
"venv/"
>>
.gitignore
echo
"__pycache__/"
>>
.gitignore
echo
"DB_PASSWORD=secret123"
>
.env
echo
"Application started"
>
application.log
git status
Expected outcome:
.env
should not appear as an untracked file.
application.log
should not appear as an untracked file.
.gitignore
should appear as an untracked file.
Students should stage and commit
.gitignore
.
Bash
git add .gitignore
git commit -m
"Add Git ignore rules"
Lab 5: Verify repository contents
Bash
git status
git log --oneline
git ls-files
git check-ignore -v .env application.log
Expected outcome:
Working tree should be clean.
Commit history should show three commits.
.env
and
application.log
should not appear in tracked files.
git check-ignore
should show the matching ignore rules.
J. BREAK AND FIX – Troubleshooting challenge
Failure-based learning
Teach students to follow this approach:
BREAK → OBSERVE → TROUBLESHOOT → FIX → VERIFY
Challenge 1: Git identity is not configured
Initial condition:
Git is installed, repository is initialized, but the developer has not configured their identity.
Execute:
Bash
git config --global --unset user.name
git config --global --unset user.email
Create a file and attempt to commit:
Bash
echo
"Testing Git"
>
test.txt
git add test.txt
git commit -m
"Test commit"
Expected symptom:
Git may report that it cannot auto-detect the author's identity.
Diagnosis:
Bash
git config user.name
git config user.email
Fix:
Bash
git config --global user.name
"Student Name"
git config --global user.email
"student@example.com"
Verify:
Bash
git commit -m
"Test commit"
git log
-
1
Challenge 2: Developer forgot to stage changes
Initial condition:
Bash
echo
"New application feature"
>>
app.py
Execute:
Bash
git commit -m
"Add new feature"
Expected symptom:
Plain text
nothing added to commit
Root cause:
Git commits only the changes staged in the index. The developer modified the file but did not stage it.
Fix:
Bash
git add app.py
git commit -m
"Add new feature"
Verify:
Bash
git status
git log
-
1
--oneline
Challenge 3: .gitignore is not ignoring an existing file
Initial condition:
A developer has already committed
.env
.
Later, they add
.env
to
.gitignore
.
They expect Git to stop tracking it.
Expected symptom:
The file remains tracked.
Root cause:
.gitignore
does not automatically stop tracking files already in the repository.
Fix:
Bash
git rm --cached .env
git add .gitignore
git commit -m
"Stop tracking environment configuration"
Verify:
Bash
git status
git ls-files
Explain that the local
.env
file remains on disk, but Git no longer tracks it.
K. Real-world industry scenarios
Use these examples to connect the topic to actual DevOps responsibilities.
Scenario
DevOps engineer's responsibility
Banking application deployment
Identify which commit introduced a configuration change
E-commerce application
Maintain application version history
Microservices
Manage individual service repositories
Kubernetes deployments
Track YAML manifests and configuration changes
CI/CD pipeline
Identify source commit associated with a pipeline execution
Security audit
Trace authorship and history of code changes
Important discussion:
Ask students:
A Jenkins pipeline fails after a developer changes a deployment configuration file. How would Git help investigate?
Expected answer:
Identify the failed build's source commit.
Inspect the commit history.
Compare the previous and current versions.
Identify the configuration change.
Coordinate with the developer to correct it.
Commit and verify the fix.
We will connect Git to Jenkins and CI/CD in later modules.
L. Knowledge assessment
10 MCQs
## Session 1 quiz
0/10 answered
1
.
Which type of version control system is Git?
Centralized
Distributed
File-based only
Manual
2
.
What does git init do?
Creates a GitHub account
Creates a local Git repository
Commits files
Uploads code
3
.
Which command stages changes?
git commit
git push
git add
git log
4
.
What is the purpose of the staging area?
Store remote files
Prepare changes for the next commit
Install Git
Delete files
5
.
Which command displays commit history?
git status
git log
git add
git init
6
.
Which directory stores Git repository data?
src
bin
.git
logs
7
.
What does .gitignore do?
Deletes files
Ignores matching untracked files
Removes commits
Creates branches
8
.
Which command displays unstaged changes?
git diff
git log
git init
git remote
9
.
Is GitHub the same as Git?
Yes
No
GitHub is a Git command
Git is a GitHub plugin
10
.
What does a Git commit represent?
A remote server
A recorded repository snapshot
A Linux process
A Git installation
Submit answers
M. Practical interview questions
Use these as oral questions at the end of the session.
What is a version control system and why do DevOps engineers need it?
What is the difference between centralized and distributed version control?
Why is Git called a distributed version control system?
What is the difference between Git and GitHub?
What happens internally when you execute
git init
?
What is the difference between a working directory and a staging area?
What happens when you execute
git add .
?
What is the purpose of a Git commit?
What is a Git blob?
What is the difference between
git diff
and
git diff --staged
?
What is HEAD in Git?
Why is
.gitignore
important?
Will
.gitignore
remove files that are already tracked?
What information does Git maintain in commit history?
Can developers commit changes without internet connectivity?
Trainer tip:
Don't accept only definitions. Ask students to demonstrate the relevant command and explain the result.
N. Homework and independent practice
Assignment: Build a local Git repository for a sample application.
Create this structure:
Plain text
devops-project/
├── README.md
├── src/
│   └── app.py
├── config/
│   └── application.properties
├── logs/
├── .gitignore
└── requirements.txt
Requirements:
Initialize a Git repository.
Configure Git identity.
Create at least five commits.
Modify files between commits.
Demonstrate staged and unstaged changes.
Create a
.gitignore
.
Ensure log files and
.env
are ignored.
Display commit history.
Demonstrate
git show
.
Capture screenshots of the commands and outputs.
Advanced self-learning:
Ask students to investigate:
Bash
git cat-file -p HEAD
git cat-file -p HEAD
^{
tree
}
git rev-parse HEAD
git reflog
They should explain what each command reveals. We will cover reflog in greater detail when discussing Git recovery.
O. AI-assisted learning
Teach students to attempt the problem first, then use AI to understand errors.
Prompt 1 – Understand Git architecture
Plain text
Act as a senior Git engineer.
Explain Git architecture from absolute beginner level.
Explain:
1. Working directory
2. Staging area
3. Local repository
4. HEAD
5. Blob
6. Tree
7. Commit
Show how git add and git commit work internally.
Use a practical example and a diagram.
Prompt 2 – Troubleshooting
Plain text
I am learning Git.
I executed git commit but received:
"nothing added to commit".
Explain:
1. Why this happens.
2. How to diagnose it.
3. How to fix it.
4. How to verify the fix.
Do not simply give me commands.
Explain the underlying Git workflow.
Prompt 3 – Interview preparation
Plain text
Act as a DevOps technical interviewer.
Ask me 15 Git fundamentals interview questions.
Include practical scenarios.
Ask one question at a time.
Evaluate my answer and explain what I missed.
P. Session 1 completion checklist
Use this checklist to decide whether students are ready for Session 2.
Student readiness
0
/
10
Explain centralized vs distributed VCS
Explain Git vs GitHub
Install and configure Git
Create a local Git repository
Explain working directory, staging area and local repository
Use git add, commit, status and log
Compare changes using git diff
Create and configure .gitignore
Troubleshoot Git identity error
Explain why .gitignore does not remove already tracked files
Mark each skill only after the student demonstrates it independently.
3. Overall module completion strategy
This is how all your requested topics fit within six hours.
Topic
Session
Overview of version control systems
1
Installation and setting up Git
1
Important Git commands
1
Creating and managing Git repositories
1
Git file workflow
1
.gitignore
1
Git miscellaneous commands
1
Reverting and resetting
2
Git branching strategies
2
Working with Git branching
2
Branching and merging
2
Rebase and squash
2
Git stash
2
Introduction to GitHub
3
Managing remote repositories
3
What students should achieve after all six hours:
Module outcome
Students should be able to take an application from a local working directory, maintain its version history, work with feature branches, integrate changes and publish the repository to GitHub.
They should also understand how source control supports CI/CD, infrastructure as code, Kubernetes manifests and enterprise DevOps workflows.
Important teaching decision:
Six hours is sufficient to introduce and practise the essential workflows, but students will need additional independent practice to become confident with merge conflicts, rebase, recovery and team collaboration.
We will keep each session within two hours and not move ahead until you ask.
Next: Session 2 – Git Branching, Merging, Rebase, Squash, Stash, Reset and Revert.
session2
ChatGPT said:
Module 3 – SCM with Git and GitHub
## Session 2: Git Branching, Merging, Rebase, Squash, Stash, Reset and Revert
2 hours
Intermediate Git
Hands-on + Troubleshooting
1. Session overview
Today's objective is to teach students how developers work on multiple features simultaneously without disturbing the main application code.
By the end of this session, students should be able to:
Understand why Git branches are required.
Create, switch, rename and delete branches.
Understand feature branching and common branching strategies.
Merge branches and resolve merge conflicts.
Understand merge vs rebase.
Perform squash operations.
Temporarily save unfinished changes using Git stash.
Recover from mistakes using reset, restore and revert.
Troubleshoot common branch-related problems.
Industry scenario
Imagine you are working in a banking application development team.
The production application is running successfully. Three developers are assigned different tasks:
Developer A: Implement customer registration.
Developer B: Fix a payment calculation bug.
Developer C: Add transaction history.
All three developers need to work simultaneously.
Should they modify the same production code branch directly?
No. This is where Git branching becomes important.
2. Session time allocation
Time
Topic
Duration
00–15 min
Branching concepts and strategies
15 min
15–35 min
Branch creation and management
20 min
35–55 min
Merge and merge conflicts
20 min
55–75 min
Rebase and squash
20 min
75–85 min
Git stash
10 min
85–105 min
Reset, restore and revert
20 min
105–115 min
Break and fix practical
10 min
115–120 min
Assessment and recap
5 min
Total
120 min
Part A – Git Branching
3. What is a Git branch?
Explain with a real-life analogy.
Imagine you are writing a book. The first edition is already published.
You want to experiment with a new chapter, but you don't want to disturb the published edition.
You create a separate copy of the working history to experiment with.
If everything works, you incorporate those changes into the main edition.
If it fails, you can discard the experiment without disturbing the original.
This is conceptually what branching enables.
Technical definition:
A Git branch is a movable reference to a commit. It allows developers to maintain independent lines of development within the same repository.
dev.to
Why do we need branches?
Problem
Branching solution
Multiple developers working simultaneously
Independent development
New feature development
Feature branches
Production bug
Hotfix branch
Testing upcoming releases
Release branch
Experimental implementation
Separate experiment branch
Unstable development code
Protect main branch
Important internal concept
Students should understand that a Git branch is not a complete independent copy of the project.
It is essentially a reference pointing to a commit.
When you commit on the currently checked-out branch, that branch reference moves forward to the new commit.
HEAD normally identifies the currently checked-out branch.
4. Create a practical repository
We will continue with the Session 1 project.
If students already have the repository, use it.
Otherwise create:
Bash
mkdir git-branching-lab
cd git-branching-lab
git init
git config user.name
"Student"
git config user.email
"student@example.com"
echo
"# Banking Application"
>
README.md
echo
"Application Version 1"
>
app.txt
git add
.
git commit -m
"Initial banking application"
Check:
Bash
git log --oneline
git branch
Expected output:
Plain text
* main
The branch name may differ if the student's repository was initialized with another default.
5. Creating and managing branches
Command 1: Create a branch
Bash
git branch feature-customer-registration
What happens?
Git creates a new branch reference.
It points to the current commit.
It does not switch to that branch.
Verify:
Bash
git branch
Example:
Plain text
feature-customer-registration
* main
The asterisk indicates the currently checked-out branch.
Command 2: Switch branches
Bash
git switch feature-customer-registration
This changes the currently checked-out branch.
Verify:
Bash
git branch --show-current
Expected:
Plain text
feature-customer-registration
Command 3: Create and switch in one operation
Bash
git switch -c feature-payment
Explain:
switch
: Changes branches.
-c
: Creates a new branch and switches to it.
This is a commonly used developer command.
Command 4: List branches
Bash
git branch
List local and remote-tracking branches:
Bash
git branch -a
Command 5: Rename a branch
Bash
git branch -m feature-payment feature-payment-service
The
-m
option renames the branch.
Command 6: Delete a branch
Bash
git branch -d feature-payment-service
This safely deletes a branch if Git considers it merged.
Force deletion:
Bash
git branch -D feature-payment-service
Explain the difference:
-d
: Safe deletion; warns if changes have not been merged.
-D
: Force deletion; can discard the branch's only reference to unmerged commits.
Production caution:
Never force-delete branches without checking whether their commits are required.
Part B – Git branching strategies
6. How companies manage branches
Explain that different companies use different branching strategies depending on release frequency, team size and deployment processes.
Strategy 1: Feature branching
medium.com
Workflow:
Developer creates a feature branch.
Implements a feature.
Commits changes.
Pushes the branch to a remote repository.
Creates a Pull Request.
Team reviews the changes.
Approved changes are merged into the main branch.
Example branches:
Plain text
main
feature/customer-registration
feature/payment-service
feature/transaction-history
Where used:
Teams that want isolated feature development and code reviews.
Strategy 2: Git Flow
leetrue.hashnode.dev
Git Flow is a structured branching model.
It commonly uses:
Branch
Responsibility
main
Production-ready releases
develop
Integration of upcoming features
feature/*
New functionality
release/*
Release preparation
hotfix/*
Urgent production fixes
Example:
Plain text
main
|
develop
|--- feature/customer
|--- feature/payment
|
release/2.0
|
hotfix/2.0.1
Explain the flow:
Developers create feature branches from
develop
.
Completed features are merged into
develop
.
A release branch is created when the release is ready for stabilization.
After testing, release changes are integrated into
main
and
develop
.
Hotfix branches are created to address urgent production issues.
Industry example:
An enterprise banking application with scheduled releases and formal release management may use a Git Flow-like model.
Strategy 3: Trunk-Based Development
manoskammas.co.uk
In this model:
Developers integrate changes frequently into a shared mainline (trunk).
Feature branches, if used, are short-lived.
Continuous integration validates changes.
Feature flags can hide incomplete functionality.
Example:
Plain text
main
|-- feature-a (short lived)
|-- feature-b (short lived)
|-- feature-c (short lived)
Industry example:
Cloud-native product teams deploying multiple times a day often prefer trunk-based development.
Compare the strategies
Feature
Feature branching
Git Flow
Trunk-based
Branch lifetime
Varies
Often longer
Very short
Complexity
Low to medium
Higher
Low to medium
Release structure
Flexible
Structured
Continuous
Integration frequency
Varies
Release-oriented
Frequent
Typical use
Team collaboration
Scheduled releases
Continuous delivery
Trainer's important point:
Git does not force any particular branching strategy. These are team processes implemented using Git capabilities.
Part C – Branching and merging
7. Understanding Git merge
Explain with an example.
The main application is running successfully.
A developer creates a feature branch and implements customer registration.
After testing, the feature needs to be integrated into main.
This process is called merging.
docs.vultr.com
Practical demonstration
Start with the repository:
Bash
git switch main
Create a feature branch:
Bash
git switch -c feature-customer-registration
Add a feature:
Bash
echo
"Customer Registration Module"
>>
app.txt
Stage and commit:
Bash
git add app.txt
git commit -m
"Add customer registration"
Check history:
Bash
git log --oneline --graph --all
Now return to main:
Bash
git switch main
Merge the feature:
Bash
git merge feature-customer-registration
Verify:
Bash
cat app.txt
git log --oneline --graph --all
Expected result:
The customer registration feature should now be available on main.
What happens internally during merge?
There are two common scenarios.
1. Fast-forward merge
This happens when the target branch has not moved forward since the feature branch was created.
minoolian.github.io
Git simply advances the target branch reference to the feature branch's commit.
Try:
Bash
git switch -c feature-fast-forward
echo
"Fast forward demonstration"
>>
app.txt
git add app.txt
git commit -m
"Fast forward feature"
git switch main
git merge feature-fast-forward
2. Three-way merge
This happens when both branches have new commits since their common ancestor.
lenord.me
Git identifies:
Common ancestor.
Changes on the target branch.
Changes on the source branch.
It combines the changes and, when necessary, creates a merge commit.
Command:
Bash
git merge feature-branch
A merge can also be forced to create a merge commit when a fast-forward is possible:
Bash
git merge --no-ff feature-branch
Explain
--no-ff
: It prevents fast-forward merging and creates a merge commit, preserving an explicit merge point in history.
8. Understanding merge conflicts
Important interview topic
A merge conflict happens when Git cannot automatically reconcile changes from different branches.
Real-world scenario:
Two developers modify the same line in the same application file.
Developer A changes:
Plain text
Transaction limit = 10000
Developer B changes:
Plain text
Transaction limit = 50000
Which value should Git choose?
Git cannot understand the business requirement. It asks a developer to resolve the conflict.
Practical conflict demonstration
First create a common starting point:
Bash
git switch main
echo
"Transaction limit = 10000"
>
transaction.txt
git add transaction.txt
git commit -m
"Add initial transaction limit"
Create Developer A's branch:
Bash
git switch -c feature/increase-limit
Modify the same line:
Bash
echo
"Transaction limit = 50000"
>
transaction.txt
git add transaction.txt
git commit -m
"Increase transaction limit"
Create Developer B's branch from the original main:
Bash
git switch main
git switch -c feature/restrict-limit
Modify the same line differently:
Bash
echo
"Transaction limit = 20000"
>
transaction.txt
git add transaction.txt
git commit -m
"Restrict transaction limit"
Now merge Developer A:
Bash
git switch main
git merge feature/increase-limit
Next merge Developer B:
Bash
git merge feature/restrict-limit
Expected result
Git should report a merge conflict because both branches changed the same line.
Check:
Bash
git status
Open
transaction.txt
.
It will contain markers similar to:
Plain text
<<<<<<< HEAD
Transaction limit = 50000
=======
Transaction limit = 20000
>>>>>>> feature/restrict-limit
Explain the markers:
Marker
Meaning
<<<<<<< HEAD
Current branch version
=======
Separates conflicting versions
>>>>>>> feature/restrict-limit
Incoming branch version
Resolve the conflict
Discuss the correct business decision with students.
For this lab, choose:
Plain text
Transaction limit = 30000
Edit the file and remove all conflict markers.
Then execute:
Bash
git add transaction.txt
git commit -m
"Resolve transaction limit merge conflict"
Verify:
Bash
git status
git log --oneline --graph --all
cat transaction.txt
Expected outcome:
No merge conflict remains.
The resolved file contains the agreed value.
The merge is completed.
Important:
Git cannot decide which business value is correct. The developer or authorized product owner must decide.
How to abort a merge
If you want to cancel an unresolved merge:
Bash
git merge --abort
This attempts to restore the pre-merge state.
Do not use this command after the merge has already been completed.
Part D – Git Rebase and Squash
9. What is Git rebase?
This is one of the most important concepts to explain properly.
Imagine:
Developer A creates a feature branch.
Developer B adds new commits to main.
Developer A continues developing the feature.
The feature branch is now based on an older version of main.
How can Developer A incorporate the latest main changes?
One approach is merge.
Another approach is rebase.
Definition:
Git rebase moves or replays commits from one branch onto a new base commit, creating new commit identities.
toanthien.com
Practical rebase demonstration
Create a fresh repository for this exercise:
Bash
mkdir git-rebase-lab
cd git-rebase-lab
git init
git config user.name
"Student"
git config user.email
"student@example.com"
echo
"Application v1"
>
app.txt
git add
.
git commit -m
"Initial commit"
Create a feature branch:
Bash
git switch -c feature/customer
Add a feature commit:
Bash
echo
"Customer feature"
>>
app.txt
git add app.txt
git commit -m
"Add customer feature"
Return to main:
Bash
git switch main
Add another commit on main:
Bash
echo
"Security enhancement"
>>
app.txt
git add app.txt
git commit -m
"Add security enhancement"
Now the history has diverged.
View it:
Bash
git log --oneline --graph --all
Switch to the feature branch:
Bash
git switch feature/customer
Rebase onto main:
Bash
git rebase main
Check history:
Bash
git log --oneline --graph --all
What happened?
Before rebase:
Plain text
C (feature)
/
A ------
\
B (main)
After rebase:
Plain text
A ------ B (main) ------ C' (feature)
The feature commit is replayed on top of the latest main commit.
The new commit
C'
has a different hash from the original
C
.
Why does the commit hash change?
A commit records information including:
Tree reference.
Parent commit reference(s).
Author and committer information.
Timestamps.
Commit message.
Changing the parent changes the commit object and therefore its hash.
Merge vs rebase
Merge
Rebase
Combines branch histories
Replays commits onto a new base
Can create merge commit
Creates new commit identities for replayed commits
Preserves original branch topology
Produces a more linear history
Useful for integrating shared work
Useful for updating private feature branches
Does not rewrite existing commits
Rewrites the commits being replayed
Production rule
Avoid rebasing commits that other developers are already depending on, especially shared branches. Rewriting shared history can cause duplicate or conflicting histories for collaborators.
A common safe workflow:
Bash
git switch feature/customer
git fetch origin
git rebase origin/main
This assumes
origin/main
is the correct integration branch.
10. What is Git squash?
Explain this using a real development example.
A developer works on one feature and creates five commits:
Plain text
Add customer form
Fix customer form validation
Fix typo
Update error handling
Correct validation
Do we really need all five commits in the final main branch history?
Sometimes not.
Squashing combines multiple commits into one commit.
Method 1: Interactive rebase
Suppose the current branch has three recent commits that you want to combine.
Bash
git log --oneline
Start:
Bash
git rebase -i HEAD
~
3
An editor opens with entries similar to:
Plain text
pick abc123 Add customer form
pick def456 Fix customer validation
pick ghi789 Fix error message
Change the second and third
pick
entries to
squash
or
s
:
Plain text
pick abc123 Add customer form
squash def456 Fix customer validation
squash ghi789 Fix error message
Save and close the editor.
Git will allow you to edit the combined commit message.
Final message:
Plain text
Implement customer registration feature
Verify:
Bash
git log --oneline
Explain:
Interactive rebase is useful for cleaning up a feature branch before integrating it.
Method 2: Squash merge
Another option is:
Bash
git switch main
git merge --squash feature/customer
git commit -m
"Implement customer registration"
This takes the changes from the feature branch and stages them as a single combined change for a new commit on main.
It does not create a normal merge commit linking the feature branch history into main.
Important distinction
Interactive rebase squash
Squash merge
Combines existing commits on a branch
Combines branch changes into one new staged change
Rewrites branch history
Creates a new commit on target branch
Used to clean feature history
Used to simplify integration history
Trainer question:
Can we squash commits that have already been pushed?
Yes, technically. But rewriting published history requires coordination with collaborators. Prefer squashing before publishing or merging where practical.
Part E – Git Stash
11. What is Git stash?
Explain a common developer situation.
A developer is working on a payment feature.
They have modified three files but have not completed the feature.
Suddenly, their team lead asks them to fix an urgent production issue.
They need to switch to another branch, but their current work is unfinished.
What should they do?
They can temporarily save their changes using Git stash.
Definition:
Git stash temporarily saves selected working-tree and index changes and restores the working directory to a clean state.
docs.vultr.com
Practical demonstration
Create a new repository:
Bash
mkdir git-stash-lab
cd git-stash-lab
git init
git config user.name
"Student"
git config user.email
"student@example.com"
echo
"Payment application"
>
app.txt
git add
.
git commit -m
"Initial payment application"
Create unfinished changes:
Bash
echo
"Payment feature in progress"
>>
app.txt
echo
"Temporary configuration"
>
config.txt
Check:
Bash
git status
Now stash the changes:
Bash
git stash
Expected output resembles:
Plain text
Saved working directory and index state
Verify:
Bash
git status
The working directory should be clean.
Useful stash commands
1. List saved stashes
Bash
git stash list
Example:
Plain text
stash@{0}: WIP on main
2. Apply the latest stash
Bash
git stash apply
This restores the changes but retains the stash entry.
3. Apply and remove the stash entry
Bash
git stash pop
This applies the stash and, if successful, removes that stash entry.
4. Stash with a description
Bash
git stash push -m
"Payment feature work"
5. Stash untracked files too
Bash
git stash -u
This includes untracked files.
6. Show stash changes
Bash
git stash show -p
7. Remove a specific stash
Bash
git stash drop stash
@{
0
}
8. Remove all stash entries
Bash
git stash clear
Caution
git stash clear
removes all stash entries. This is not easily reversible.
Industry scenario
A production hotfix needs immediate attention.
Plain text
Developer working on feature branch
|
v
Unfinished changes
|
v
git stash
|
v
Switch to hotfix
|
v
Fix production bug
|
v
Switch back to feature
|
v
git stash pop
|
v
Continue development
Important:
Git stash is temporary local storage, not a replacement for committing or backing up important work.
Part F – Reverting, Resetting and Restoring
12. Why do we need Git recovery commands?
Ask students:
What happens if a developer accidentally:
Modifies the wrong file?
Stages an unwanted file?
Creates a bad commit?
Commits incorrect code?
Introduces a bug into production?
Git provides multiple ways to recover.
However, students must understand that
restore
,
reset
and
revert
solve different problems.
13. Understanding git restore
git restore
is used to restore file contents in the working tree or staging area.
Scenario 1: Undo unstaged changes
Start with a clean repository:
Bash
echo
"Original application"
>
app.txt
git add app.txt
git commit -m
"Add application"
Modify the file:
Bash
echo
"Incorrect changes"
>
app.txt
Check:
Bash
git status
git diff
Discard the unstaged modifications:
Bash
git restore app.txt
Verify:
Bash
cat app.txt
git status
The file returns to the version recorded in the index.
Caution
This discards the unstaged changes to that file. Git may not be able to recover them afterward.
Scenario 2: Unstage a file
Suppose you accidentally staged a file:
Bash
echo
"Temporary data"
>
temp.txt
git add temp.txt
Unstage it:
Bash
git restore --staged temp.txt
Verify:
Bash
git status
The file remains in your working directory, but it is no longer staged.
Important distinction:
git restore file.txt
: Restores working-tree content.
git restore --staged file.txt
: Removes the file's changes from the staging area while preserving working-tree content.
14. Understanding git reset
This command is very important and must be taught carefully.
git reset
moves the current branch reference to another commit. Depending on the reset mode, it also changes the index and working tree.
Consider this history:
Plain text
A → B → C
^
HEAD
You want to move back to commit B.
There are three commonly used reset modes.
Mode 1: Soft reset
Bash
git reset --soft HEAD
~
1
What happens?
HEAD moves to the previous commit.
The previous commit is no longer at the branch tip.
Its changes remain staged.
datacamp.com
Example:
Bash
git log --oneline
git reset --soft HEAD
~
1
git status
The removed commit's changes should appear staged.
Use case:
You want to undo the last commit but retain the changes ready for a new commit.
Mode 2: Mixed reset
Bash
git reset --mixed HEAD
~
1
This is the default mode when no mode is specified.
What happens?
HEAD moves backward.
Index is reset to the target commit.
Working-tree files are preserved.
git-scm.com
Example:
Bash
git reset --mixed HEAD
~
1
git status
The removed commit's changes should appear as unstaged modifications or untracked files, depending on the files involved.
Use case:
You want to undo the commit but retain your changes in the working directory.
Mode 3: Hard reset
Bash
git reset --hard HEAD
~
1
What happens?
HEAD moves backward.
Index is reset.
Tracked working-tree files are reset to match the target commit.
git-scm.com
Example:
Bash
git reset --hard HEAD
~
1
Use case:
You intentionally want to discard changes in the index and tracked working tree and move the branch to an earlier commit.
Destructive operation
Uncommitted changes can be permanently lost. Untracked files are generally not removed by
git reset --hard
. Never demonstrate this on a student's important project.
Compare all three modes
Mode
HEAD
Staging area
Working directory
--soft
Moves back
Preserved
Preserved
--mixed
Moves back
Reset
Preserved
--hard
Moves back
Reset
Tracked files reset
Practical reset lab
Create a separate test repository:
Bash
mkdir reset-lab
cd reset-lab
git init
git config user.name
"Student"
git config user.email
"student@example.com"
echo
"Version 1"
>
app.txt
git add
.
git commit -m
"Version 1"
echo
"Version 2"
>>
app.txt
git add
.
git commit -m
"Version 2"
echo
"Version 3"
>>
app.txt
git add
.
git commit -m
"Version 3"
git log --oneline
Now demonstrate soft reset:
Bash
git reset --soft HEAD
~
1
git status
Explain why the Version 3 changes are staged.
To repeat the experiment from a clean baseline, recreate the test repository or reset it using a known reference commit. Do not blindly repeat reset commands against an unfamiliar history.
15. Understanding git revert
This is particularly important for enterprise and production environments.
Imagine a developer has committed a change and pushed it to the shared repository.
The change causes a production problem.
Should the developer move the shared branch backward using
git reset
?
Usually, no.
Instead, they can use
git revert
.
Definition:
Git revert creates a new commit that reverses the changes introduced by an earlier commit.
stackoverflow.com
Practical demonstration
Bash
mkdir revert-lab
cd revert-lab
git init
git config user.name
"Student"
git config user.email
"student@example.com"
echo
"Application version 1"
>
app.txt
git add
.
git commit -m
"Initial application"
Add a feature:
Bash
echo
"Incorrect payment calculation"
>>
app.txt
git add
.
git commit -m
"Add payment calculation"
View history:
Bash
git log --oneline
Identify the commit hash associated with the incorrect feature.
Revert it:
Bash
git revert
<
commit-hash
>
Git creates a new commit that reverses that commit's changes.
Verify:
Bash
git log --oneline
cat app.txt
The original commit remains in history. The new revert commit reverses its changes.
Reset vs revert
Feature
Reset
Revert
Changes branch history
Yes
No, adds a new commit
Creates new commit
No
Yes
Common usage
Local cleanup
Shared history correction
Safe for shared branches
Usually avoid rewriting shared history
Generally suitable
Removes original commit from branch history
Yes, moves branch away from it
No
Production example:
A banking application deployment introduces an incorrect interest calculation.
The team identifies the commit that introduced the bug.
The team creates a revert commit, tests the application and deploys the corrected version.
This maintains an auditable history of both the original change and the correction.
Part G – Git miscellaneous commands
16. Commands students should know
Command
Explanation
git show HEAD
Display latest commit details
git reflog
View recent movements of HEAD and references
git blame app.py
Identify line-level authorship
git clean -n
Preview untracked files/directories that would be removed
git clean -f
Remove untracked files
git diff HEAD
Compare working tree against HEAD
git log --oneline
Compact commit history
git log --graph --all
Visualize commit history
git branch -v
Show local branches and latest commits
git status -sb
Short branch-aware status
Important: git reflog
Explain this with a recovery scenario.
A developer accidentally executes:
Bash
git reset --hard HEAD
~
2
They realize that two commits are no longer visible in the current branch history.
Can Git help locate the previous branch position?
Yes, often through reflog.
Bash
git reflog
Example:
Plain text
abc1234 HEAD@{0}: reset: moving to HEAD~2
def5678 HEAD@{1}: commit: Add transaction module
ghi9012 HEAD@{2}: commit: Add customer module
The developer can identify the previous commit reference.
A recovery approach in a disposable lab:
Bash
git branch recovery-branch def5678
This creates a branch pointing to the recovered commit.
Important:
Reflog is local reference history, not a permanent backup. Entries expire, and unreachable objects can eventually be garbage-collected.
Part H – Complete hands-on practical
17. Industry-based Git challenge
Mandatory practical – 10 minutes
Scenario: Banking application development team
You are a developer in a banking company.
Your team has asked you to:
Create a feature branch.
Implement a customer feature.
Commit your changes.
Simulate another developer changing the same file.
Resolve a merge conflict.
Integrate the feature into main.
Demonstrate how to recover an incorrect commit.
Students should use a disposable repository.
Step 1: Create the project
Bash
mkdir banking-git-project
cd banking-git-project
git init
git config user.name
"Student"
git config user.email
"student@example.com"
echo
"Banking Application"
>
README.md
echo
"Customer Module"
>
customer.txt
git add
.
git commit -m
"Initial banking application"
Step 2: Create Developer A's branch
Bash
git switch -c feature/customer-registration
echo
"Customer registration enabled"
>>
customer.txt
git add
.
git commit -m
"Implement customer registration"
Step 3: Create Developer B's branch
Bash
git switch main
git switch -c feature/customer-validation
echo
"Customer validation enabled"
>>
customer.txt
git add
.
git commit -m
"Implement customer validation"
Step 4: Merge Developer A's branch
Bash
git switch main
git merge feature/customer-registration
Step 5: Merge Developer B's branch
Bash
git merge feature/customer-validation
Students should encounter a merge conflict because both branches modified the same file.
Step 6: Resolve the conflict
Open
customer.txt
.
Keep both required functionalities:
Plain text
Customer Module
Customer registration enabled
Customer validation enabled
Save the file.
Execute:
Bash
git add customer.txt
git commit -m
"Resolve customer feature merge conflict"
Step 7: Verify the result
Bash
git status
git log --oneline --graph --all
cat customer.txt
Expected outcome:
Both features are present.
Merge conflict is resolved.
Commit history is available.
Working tree is clean.
Part I – Assessment and interview preparation
18. Knowledge-check questions
Ask these questions verbally.
What is a Git branch internally?
Does creating a branch duplicate the complete repository?
What is the difference between
git branch
and
git switch
?
What is a fast-forward merge?
What is a three-way merge?
Why do merge conflicts occur?
How do you abort a merge?
What is the difference between merge and rebase?
Why does a rebase generate new commit hashes?
What is Git squash?
What is the difference between
git stash apply
and
git stash pop
?
What is the difference between
git reset --soft
and
git reset --hard
?
What is the difference between reset and revert?
Which command should generally be preferred when undoing a problematic commit already shared with a team?
What is Git reflog?
19. Scenario-based interview questions with answers
Q1. Two developers modify the same line in a file. What happens when they merge their branches?
Answer: Git may report a merge conflict because it cannot automatically reconcile the changes. A developer must inspect and resolve the conflicting content.
Q2. Your feature branch is three commits behind main. How will you update it?
Answer:
Bash
git switch feature-branch
git fetch origin
git rebase origin/main
Alternatively:
Bash
git merge origin/main
The choice depends on the team's branching policy.
Q3. You accidentally committed a password. What will you do?
Answer:
Immediately rotate or revoke the exposed credential.
Follow the company's security incident process.
Remove the secret from the current source.
Assess Git history and other copies.
Coordinate history cleanup if required.
Add appropriate
.gitignore
rules and secret scanning.
A normal revert or file deletion does not remove a secret from historical commits.
Q4. You committed three times while developing one feature. Your team wants one clean commit. What will you do?
Answer:
Bash
git rebase -i HEAD
~
3
Use squash to combine the commits, assuming the commits are safe to rewrite.
Q5. You are working on a feature and your manager asks you to fix a production bug immediately. What will you do?
Answer:
Bash
git stash push -m
"Unfinished feature"
git switch main
git switch -c hotfix/payment-issue
After fixing and committing the hotfix, return to the feature branch and restore the stash.
Q6. A developer pushed a bad commit to a shared branch. Should you use reset?
Answer: Generally, use
git revert
because it creates a new commit that reverses the changes without rewriting the shared history.
Q7. You accidentally executed
git reset --hard
. Can you recover?
Answer: Check
git reflog
for the previous commit reference. Recovery is possible if the commit object still exists.
Q8. What is the difference between a branch and a tag?
Answer: A branch is a movable reference that normally advances as new commits are made. A tag is generally a fixed reference to a particular commit, commonly used to mark releases.
20. Homework – Advanced Git practice
Students must complete the following independently.
Exercise
Required skill
Create three feature branches
Branch management
Make two commits in each branch
Commit history
Merge all branches into main
Integration
Create and resolve two merge conflicts
Troubleshooting
Rebase a feature branch
History management
Squash three commits into one
Clean history
Stash unfinished changes
Temporary work management
Demonstrate soft reset
Recovery
Demonstrate mixed reset
Recovery
Demonstrate hard reset in disposable repository
Recovery
Revert an incorrect commit
Safe correction
Recover a previous branch position using reflog
Advanced recovery
AI practice prompt
Plain text
Act as a senior DevOps engineer and Git interviewer.
Give me 20 real-world Git troubleshooting scenarios.
Cover:
- Branching
- Merge conflicts
- Rebase
- Squash
- Stash
- Reset
- Revert
- Reflog
Give me one scenario at a time.
Do not provide the solution immediately.
Let me explain my approach first.
Evaluate my answer based on production safety,
Git understanding and troubleshooting methodology.
21. Session 2 completion checklist
## Session 2 readiness
0
/
11
Explain why Git branching is needed
Create, switch, rename and delete branches
Explain Git Flow and trunk-based development
Perform fast-forward and three-way merges
Resolve merge conflicts independently
Explain merge versus rebase
Perform interactive rebase and squash
Use git stash and restore changes
Explain reset soft, mixed and hard
Use git revert to reverse a commit
Explain git reflog and recover a commit
22. Trainer's final revision – Commands to remember
Operation
Command
Create branch
git branch feature-x
Create and switch
git switch -c feature-x
Switch branch
git switch main
Delete branch
git branch -d feature-x
Merge branch
git merge feature-x
Abort merge
git merge --abort
Rebase
git rebase main
Interactive rebase
git rebase -i HEAD~3
Squash merge
git merge --squash feature-x
Stash
git stash
Restore stash
git stash pop
Unstage changes
git restore --staged file.txt
Discard unstaged changes
git restore file.txt
Soft reset
git reset --soft HEAD~1
Mixed reset
git reset --mixed HEAD~1
Hard reset
git reset --hard HEAD~1
Revert commit
git revert commit-hash
View reflog
git reflog
23. What students should understand before Session 3
There is one important transition you should explain.
So far, students have worked with local Git repositories.
But in an actual company, developers need to share their changes with other developers.
This introduces remote repositories.
codelearn.io
The next session will cover:
What GitHub is and why companies use it.
Local repository vs remote repository.
Creating GitHub repositories.
git remote add origin
.
git push
.
git pull
.
git fetch
.
git clone
.
Origin and upstream.
Tracking branches.
GitHub collaboration and Pull Requests.
Practical multi-developer collaboration.
One important distinction to tell students:
A successful local Git commit does not mean the changes have been uploaded to GitHub. Uploading and synchronizing changes with a remote repository is a separate workflow.
## Session 2 completed
Trainer recommendation:
Give students the homework before starting Session 3. Make them resolve at least one merge conflict independently. Merge conflict troubleshooting is much more valuable than memorizing Git commands.
start session 3
ChatGPT said:
Module 3 – SCM with Git and GitHub
## Session 3: GitHub and Remote Repository Management
2 hours
Beginner to Industry-ready
Hands-on + Collaboration
medium.com
1. Session overview
In Sessions 1 and 2, students learned how to manage source code locally using Git.
Today, we will move from individual development to team collaboration using GitHub.
The main objective:
Students should independently create a GitHub repository, connect their local repository, push code, retrieve changes and understand how multiple developers collaborate through remote repositories.
### Learning objectives
By the end of this session, students should be able to:
Explain what GitHub is and how it works with Git.
Differentiate local and remote repositories.
Create and configure a GitHub repository.
Connect local Git repositories to remote repositories.
Understand
origin
and
upstream
.
Execute
git clone
,
push
,
pull
and
fetch
.
Understand remote-tracking branches.
Configure authentication using SSH or HTTPS.
Understand GitHub Pull Requests and code reviews.
Troubleshoot common remote repository errors.
2. Two-hour session time allocation
Time
Topic
Duration
00–15 min
GitHub fundamentals and architecture
15 min
15–30 min
Create GitHub repository and authentication
15 min
30–50 min
Connecting local and remote repositories
20 min
50–70 min
Push, pull, fetch and clone
20 min
70–85 min
Branches, upstream and tracking
15 min
85–100 min
Pull Requests and collaboration
15 min
100–115 min
Complete hands-on lab and troubleshooting
15 min
115–120 min
Assessment and recap
5 min
Total
120 min
Part A – Understanding GitHub
3. What is GitHub?
Start with a question:
Suppose you are working on an application locally.
You have:
Created a Git repository.
Made 20 commits.
Created three branches.
Implemented two features.
Fixed several bugs.
Now your team lead asks:
"How can the other developers access your code?"
Your local repository is stored on your computer.
Other developers cannot automatically access it.
You need a shared remote repository.
This is where GitHub comes into the picture.
Definition:
GitHub
is a cloud-based platform that hosts Git repositories and provides collaboration capabilities for software development.
It provides:
Repository hosting.
Pull Requests.
Code reviews.
Issue tracking.
Branch protection.
GitHub Actions for CI/CD.
Release management.
Project management and collaboration.
Git vs GitHub
Git
Version control software.
Runs locally.
Maintains commit history.
Manages branches.
Works offline for local operations.
GitHub
Repository hosting platform.
Provides remote collaboration.
Hosts Git repositories.
Supports Pull Requests.
Provides automation and project tools.
Important:
GitHub does not replace Git. GitHub hosts Git repositories and adds collaboration and automation features.
Other platforms providing similar capabilities include:
GitLab
Bitbucket
Azure Repos
4. How local and remote repositories work
codelearn.io
Explain the architecture:
Developer workstation
Contains:
Working directory.
Staging area.
Local Git repository.
Local branches.
GitHub server
Contains:
Remote Git repository.
Remote branches.
Commit history.
Collaboration features.
Developers exchange commits between local and remote repositories.
Important operations
Operation
What it does
Clone
Creates a local repository from a remote repository
Push
Sends local commits to a remote repository
Fetch
Downloads remote updates without integrating them into the current branch
Pull
Fetches and integrates remote changes
Remote
Manages remote repository references
Real-world scenario
Imagine a team with three developers:
Plain text
GitHub Repository
|
-------------------
|        |        |
Dev A     Dev B    Dev C
|        |        |
Local    Local    Local
Repo     Repo     Repo
Each developer has their own local repository.
When Developer A pushes code, the changes become available on GitHub.
Developer B can fetch or pull those changes.
This is the foundation of distributed development.
Part B – Create a GitHub repository
5. Create your GitHub account
Ask students to open:
GitHub official website
Instructions:
Create an account if they don't already have one.
Sign in.
Click the
+
icon.
Select New repository.
Enter the repository name:
Plain text
devops-github-lab
6. Add a description:
Plain text
Hands-on Git and GitHub learning project
7. Choose Public or Private.
Explain the difference:
Public repository
Private repository
Publicly accessible
Restricted to authorized users
Anyone can view
Only authorized users can access
Suitable for open-source projects
Suitable for proprietary projects
8. For this demonstration, create an empty repository.
Trainer recommendation
Do not initialize the GitHub repository with a README,
.gitignore
or license for this particular exercise. We want to demonstrate connecting an existing local repository to an empty remote repository without introducing unrelated initial histories.
Click Create repository.
Students should now see a GitHub repository page with connection instructions.
Part C – Authentication: How Git communicates with GitHub
6. How does Git authenticate with GitHub?
A common beginner question:
"If I execute
git push
, how does Git know whether I am authorized to upload code to GitHub?"
Git needs authentication.
There are two commonly used methods.
HTTPS authentication using a Personal Access Token (PAT).
SSH authentication using SSH keys.
Method 1: HTTPS authentication
A remote repository URL looks like:
Plain text
https://github.com/username/devops-github-lab.git
When pushing, GitHub needs to authenticate the user.
GitHub no longer accepts ordinary account passwords for Git operations over HTTPS.
Instead, users can authenticate using a Personal Access Token (PAT), typically managed through a credential manager.
Explain:
Username identifies the account.
PAT provides an authentication credential.
Git Credential Manager can securely store and manage credentials.
Official documentation:
GitHub authentication documentation
Trainer note:
Never ask students to share their tokens with you or commit them into a repository.
Method 2: SSH authentication
rahul-aerodestiny.github.io
Explain SSH using a real-life analogy.
Imagine you have a lock and key.
The public key is registered with GitHub.
The private key stays on your computer.
GitHub challenges your computer to prove possession of the matching private key.
The SSH client uses the private key to authenticate.
The private key must never be uploaded to GitHub.
Step 1: Check whether an SSH key already exists
For Linux, macOS, Git Bash or Windows:
Bash
ls -la ~/.ssh
Look for files such as:
Plain text
id_ed25519
id_ed25519.pub
The
.pub
file is the public key.
The file without
.pub
is the private key.
Step 2: Generate an SSH key
Bash
ssh-keygen -t ed25519 -C
"student@example.com"
Explain the arguments:
ssh-keygen
: Generates SSH keys.
-t ed25519
: Uses the Ed25519 key algorithm.
-C
: Adds a descriptive comment.
Accept the default file location or choose another appropriate path.
Use a passphrase when possible.
Step 3: Start SSH agent and add the key
For Git Bash on Windows:
Bash
eval
"
$(
ssh-agent -s
)
"
Add the private key:
Bash
ssh-add ~/.ssh/id_ed25519
For Windows PowerShell, the OpenSSH Authentication Agent service can be used instead.
Step 4: Copy the public key
Bash
cat ~/.ssh/id_ed25519.pub
Copy the complete public key.
On GitHub:
Open Settings.
Select SSH and GPG keys.
Click New SSH key.
Give it a descriptive title.
Paste the public key.
Save.
Step 5: Test the connection
Bash
ssh -T git
@
github.com
Expected successful output resembles:
Plain text
Hi username! You've successfully authenticated,
but GitHub does not provide shell access.
Explain that GitHub has verified the SSH authentication. It does not provide a general-purpose shell.
Which authentication method should companies use?
Both are widely used. SSH keys and HTTPS with securely managed tokens are valid approaches. Organizational policy determines the preferred method.
Part D – Connect a local repository to GitHub
7. Understanding git remote
Before running the command, explain:
A remote is a named reference to another Git repository.
For example:
Plain text
origin → https://github.com/username/devops-github-lab.git
origin
is simply a conventional remote name. It is not a special Git keyword.
Step 1: Create a local project
If students have completed the earlier sessions, they can reuse their existing project.
For a clean demonstration:
Bash
mkdir devops-github-lab
cd devops-github-lab
git init
Create files:
Bash
echo
"# DevOps GitHub Lab"
>
README.md
echo
"print('Hello from GitHub')"
>
app.py
Commit:
Bash
git add
.
git commit -m
"Initial commit"
Verify:
Bash
git status
git log --oneline
Step 2: Connect to the GitHub repository
Copy the repository URL from GitHub.
For HTTPS:
Bash
git remote add origin https
:
//github.com/username/devops-github-lab.git
For SSH:
Bash
git remote add origin git
@
github.com
:
username/devops-github-lab.git
Explain the command:
Component
Meaning
git
Git command
remote
Remote repository management
add
Add a remote reference
origin
Name assigned to the remote
URL
Address of the remote repository
Step 3: Verify the remote
Bash
git remote
Expected:
Plain text
origin
Show detailed information:
Bash
git remote -v
Expected:
Plain text
origin  https://github.com/username/devops-github-lab.git (fetch)
origin  https://github.com/username/devops-github-lab.git (push)
The actual URL depends on the authentication method and repository.
Other useful remote commands
Bash
# Display remote information
git remote show origin
# Change remote URL
git remote set-url origin
<
new-url
>
# Rename a remote
git remote rename origin github
# Remove a remote reference
git remote remove github
Explain that removing a remote reference does not delete the remote repository on GitHub.
8. Understanding git push
Now students have:
A local Git repository.
At least one local commit.
A GitHub remote configured as
origin
.
But the code is not yet uploaded.
This is where
git push
is used.
Step 1: Check the branch name
Bash
git branch --show-current
Assume the output is:
Plain text
main
Step 2: Push the local branch
Bash
git push -u origin main
Explain each component:
Component
Meaning
git push
Upload commits to a remote
-u
Set upstream tracking information
origin
Remote name
main
Local branch being pushed
What happens internally?
Git checks the destination remote.
Git authenticates with GitHub.
Git identifies the commits that the remote needs.
Required Git objects are transferred.
GitHub updates the remote branch reference if the update is permitted.
The local branch is configured to track the remote branch when
-u
is used.
leandronsp.com
What is upstream?
Explain carefully.
When students execute:
Bash
git push -u origin main
Git establishes
origin/main
as the upstream tracking branch for the local
main
branch.
This means Git knows which remote branch is associated with the local branch.
After configuring upstream, students can usually execute:
Bash
git push
without specifying the remote and branch again.
Check:
Bash
git branch -vv
Example:
Plain text
* main abc1234 [origin/main] Initial commit
Explain:
main
: Local branch.
abc1234
: Latest local commit.
origin/main
: Its upstream tracking branch.
Initial commit
: Latest commit message.
Important distinction:
A remote name is not the same as an upstream branch.
origin
: A remote repository name.
origin/main
: A remote-tracking branch.
Upstream: The configured tracking relationship for a local branch.
Part E – Clone, Fetch and Pull
9. Understanding git clone
Scenario:
A new developer joins your company.
The application source code already exists on GitHub.
The developer needs to download the project and start working.
Should they execute
git init
and manually recreate every file?
No. They use
git clone
.
Definition:
git clone
creates a local copy of an existing Git repository, including its commit history and relevant remote-tracking references.
Practical demonstration
Open PowerShell or Git Bash in another directory.
Bash
git clone https
:
//github.com/username/devops-github-lab.git
Or use SSH:
Bash
git clone git
@
github.com
:
username/devops-github-lab.git
Git creates:
Plain text
devops-github-lab/
├── .git/
├── README.md
└── app.py
Navigate:
Bash
cd devops-github-lab
Verify:
Bash
git remote -v
git branch -a
git log --oneline
Explain what clone does internally:
Creates a local repository.
Downloads the required Git objects.
Sets up a remote, normally named
origin
.
Creates a local branch for the default remote branch.
Configures upstream tracking for that branch.
Interview question:
What is the difference between
git init
and
git clone
?
Answer:
git init
initializes a new local repository.
git clone
creates a local repository from an existing remote repository.
10. Understanding git fetch
This is one of the most misunderstood commands.
Scenario:
Developer A has pushed new code to GitHub.
Developer B wants to know what changes are available before incorporating them into their local branch.
They can use
git fetch
.
Definition:
git fetch
downloads new objects and updates remote-tracking references without merging those changes into the current local branch.
dev.to
Practical demonstration
In Developer A's working copy, create a change:
Bash
echo
"New feature added by Developer A"
>>
README.md
git add README.md
git commit -m
"Add feature documentation"
git push
In Developer B's working copy:
Bash
git fetch origin
Now check:
Bash
git status
git log --oneline --graph --all
Students should see that
origin/main
may have advanced, but their current local
main
has not automatically incorporated the new commit.
To compare:
Bash
git diff main origin/main
This shows the difference between local
main
and the fetched remote-tracking branch.
Important concept: What is origin/main?
Explain:
origin/main
is a local remote-tracking reference that represents the last fetched state of the remote's
main
branch.
It is not a live view of GitHub. It updates when Git fetches or performs another operation that fetches remote updates.
11. Understanding git pull
Now ask:
"If fetch downloads changes, how do I actually integrate those changes into my local branch?"
Answer:
git pull
.
Definition:
git pull
fetches changes from a remote repository and integrates them into the current branch, usually through merge or rebase depending on configuration and command options.
Command
Bash
git pull origin main
If the local branch tracks
origin/main
, students can generally use:
Bash
git pull
What happens internally?
Plain text
git pull
|
v
git fetch
|
v
Download remote changes
|
v
Integrate changes
|
v
Update current local branch
medium.com
Fetch vs Pull
Feature
Fetch
Pull
Downloads remote updates
Yes
Yes
Updates remote-tracking branches
Yes
Yes
Integrates into current branch
No
Yes
Allows inspection before integration
Yes
Not by default
Useful for controlled troubleshooting
Yes
Yes
Trainer recommendation:
Teach students to use
git fetch
before
git pull
when they want to inspect remote changes before integration.
Part F – Understanding upstream and remote-tracking branches
12. Origin vs upstream
This is an important topic for students who will work on enterprise GitHub repositories.
Consider two developers:
Developer A owns a repository.
Developer B forks that repository and contributes changes.
hetul-patel.github.io
Explain:
Origin
Usually refers to the remote repository from which a local repository was cloned.
Upstream
Often refers to the original repository from which a fork was created.
Example:
Developer A owns:
Plain text
company/banking-application
Developer B forks it:
Plain text
developer-b/banking-application
Developer B clones their fork.
Their local configuration may look like:
Plain text
origin   → developer-b/banking-application
upstream → company/banking-application
Add the original repository:
Bash
git remote add upstream https
:
//github.com/company/banking-application.git
Verify:
Bash
git remote -v
Expected structure:
Plain text
origin    https://github.com/developer-b/banking-application.git
upstream  https://github.com/company/banking-application.git
Fetch updates from the original repository:
Bash
git fetch upstream
Update the local main branch using the original repository:
Bash
git switch main
git merge upstream/main
Or, if the local main branch is suitable for history rewriting:
Bash
git rebase upstream/main
Important:
origin
and
upstream
are conventional names, not reserved keywords. Their meaning depends on how the remotes are configured.
13. Understanding remote-tracking branches
Students often confuse these three:
Plain text
main
origin/main
origin/feature-payment
Explain the difference:
Name
Meaning
main
Local branch
origin/main
Local reference tracking remote main
origin/feature-payment
Local reference tracking remote feature-payment
View all branches:
Bash
git branch -a
View local branches with tracking information:
Bash
git branch -vv
View remote-tracking branches:
Bash
git branch -r
Create a local branch tracking a remote branch
Bash
git switch --track origin/feature-payment
Alternatively:
Bash
git switch -c feature-payment --track origin/feature-payment
Explain that tracking allows Git to associate a local branch with its corresponding remote branch.
Part G – GitHub collaboration and Pull Requests
14. What is a Pull Request?
Very important for industry interviews
Explain using a company scenario.
A developer has completed a payment feature.
Should the developer directly push the feature into the production branch?
Most enterprise teams require code review before integration.
This is where a Pull Request (PR) is used.
Definition:
A Pull Request is a GitHub collaboration mechanism that proposes changes from one branch into another branch for review and integration.
medium.com
Typical Pull Request workflow
Developer creates a feature branch.
Developer implements a feature.
Developer commits changes.
Developer pushes the feature branch to GitHub.
Developer opens a Pull Request.
Reviewers inspect the changes.
Reviewers provide comments or request changes.
Developer updates the branch.
Required checks pass.
Authorized team members merge the PR.
Practical demonstration
Create a feature branch:
Bash
git switch -c feature/payment-api
Modify the application:
Bash
echo
"Payment API module"
>>
app.py
Commit:
Bash
git add app.py
git commit -m
"Add payment API module"
Push the branch:
Bash
git push -u origin feature/payment-api
Now open GitHub.
Students should:
Navigate to their repository.
Select Pull Requests.
Click New Pull Request.
Choose
main
as the base branch.
Choose
feature/payment-api
as the compare branch.
Review the changes.
Create the Pull Request.
Explain the terms:
Term
Meaning
Base
Branch receiving the proposed changes
Compare
Branch containing the proposed changes
Reviewer
Person asked to review the code
Assignee
Person responsible for the PR
Merge
Integrate approved changes
Review comments
Feedback on the proposed changes
What happens during code review?
Reviewers look for:
Coding standards.
Incorrect business logic.
Security vulnerabilities.
Hardcoded credentials.
Unnecessary code.
Missing tests.
Configuration mistakes.
Performance concerns.
What is branch protection?
In enterprise environments, teams may protect the main branch.
Typical rules include:
Require Pull Requests.
Require approvals.
Require successful CI checks.
Require conversations to be resolved.
Restrict direct pushes.
GitHub documentation:
GitHub protected branches documentation
Connect GitHub to DevOps
This is where you should introduce GitHub Actions without teaching it in detail.
linkedin.com
Explain the relationship:
Plain text
Developer
|
v
Git commit
|
v
Push to GitHub
|
v
Pull Request
|
v
GitHub Actions
|
+---- Build
|
+---- Unit Tests
|
+---- Security Scanning
|
+---- Quality Checks
|
v
Code Review
|
v
Merge to Main
|
v
Deployment Pipeline
Important:
GitHub is not itself a CI/CD pipeline. GitHub Actions is one of the automation capabilities available within GitHub.
Part H – Complete hands-on laboratory
15. Lab: Two developers collaborating through GitHub
Mandatory practical
Industry scenario:
A company is developing a banking application.
Two developers need to contribute to the same repository.
Developer A creates a customer module.
Developer B creates a payment module.
Both developers push their changes to GitHub.
A Pull Request is used to review and integrate changes.
You can demonstrate this using two separate working directories on one computer, or two student computers.
Step 1: Developer A creates the repository
Bash
mkdir banking-devops-project
cd banking-devops-project
git init
git config user.name
"Developer A"
git config user.email
"developer-a@example.com"
echo
"# Banking Application"
>
README.md
git add
.
git commit -m
"Initial banking application"
Connect to the empty GitHub repository:
Bash
git remote add origin https
:
//github.com/username/banking-devops-project.git
Push:
Bash
git push -u origin main
Step 2: Developer B clones the repository
On another computer or in another directory:
Bash
git clone https
:
//github.com/username/banking-devops-project.git
Navigate:
Bash
cd banking-devops-project
Verify:
Bash
git remote -v
git branch -a
Developer B now has a local copy of the repository.
Step 3: Developer A creates a feature branch
Bash
git switch -c feature/customer-service
Create a file:
Bash
echo
"Customer service implementation"
>
customer.py
Commit:
Bash
git add customer.py
git commit -m
"Add customer service"
Push:
Bash
git push -u origin feature/customer-service
Step 4: Developer B creates another feature branch
Bash
git switch -c feature/payment-service
Create a file:
Bash
echo
"Payment service implementation"
>
payment.py
Commit:
Bash
git add payment.py
git commit -m
"Add payment service"
Push:
Bash
git push -u origin feature/payment-service
Step 5: Create Pull Requests
On GitHub:
Developer A opens a PR from
feature/customer-service
to
main
.
Developer B opens a PR from
feature/payment-service
to
main
.
Students should inspect:
Changed files.
Commit history.
PR descriptions.
Review comments.
Merge options.
Merge both Pull Requests after review.
Step 6: Synchronize both developers
Developer A:
Bash
git switch main
git pull origin main
Developer B:
Bash
git switch main
git pull origin main
Verify:
Bash
git log --oneline --graph --all
ls
Expected files:
Plain text
README.md
customer.py
payment.py
Both developers should now have the integrated application locally.
Part I – BREAK AND FIX: GitHub troubleshooting
16. Common real-world errors
These are particularly useful for junior DevOps interviews.
Challenge 1: Authentication failed
Scenario:
Developer executes:
Bash
git push origin main
Error resembles:
Plain text
remote: Invalid username or token
fatal: Authentication failed
Possible root causes:
Invalid or expired Personal Access Token.
Incorrect credential stored in Git Credential Manager.
Insufficient repository permissions.
Incorrect remote URL.
Diagnosis:
Bash
git remote -v
git config --get credential.helper
Resolution:
Verify the repository URL.
Verify the user's repository access.
Generate or configure an appropriate authentication credential.
Remove outdated credentials from the credential manager if necessary.
Retry the push.
Never paste tokens into terminal commands or share them in screenshots.
Challenge 2: Rejected push – non-fast-forward
Scenario:
Developer tries to push code.
Bash
git push origin main
Error:
Plain text
! [rejected] main -> main (non-fast-forward)
What happened?
Another developer pushed changes to GitHub, and the local branch does not contain those remote commits.
Git rejects the push to avoid overwriting remote history.
Diagnosis:
Bash
git fetch origin
git log --oneline --graph --all
Fix:
Bash
git pull --rebase origin main
Resolve any conflicts if they occur.
Then:
Bash
git push origin main
Important:
Do not blindly use
git push --force
to resolve a rejected push.
Challenge 3: Remote origin already exists
Scenario:
Bash
git remote add origin https
:
//github.com/user/project.git
Error:
Plain text
error: remote origin already exists.
Root cause:
A remote named
origin
is already configured.
Diagnosis:
Bash
git remote -v
Fix:
If the existing remote is incorrect:
Bash
git remote set-url origin https
:
//github.com/user/project.git
Verify:
Bash
git remote -v
Challenge 4: Repository not found
Error:
Plain text
fatal: repository not found
Possible causes:
Incorrect repository URL.
Repository does not exist.
Private repository without sufficient permissions.
Authentication problem.
Check:
Bash
git remote -v
Verify the repository URL in GitHub and confirm access.
Challenge 5: Failed to push some refs
Possible message:
Plain text
error: failed to push some refs
Explain that this is a general rejection message. It is not enough to identify the root cause.
Ask students to inspect the preceding error output.
Possible causes include:
Non-fast-forward update.
Branch protection rules.
Insufficient permissions.
Repository rules or policy restrictions.
The troubleshooting approach should be based on the actual error, not a blindly executed command.
Challenge 6: Accidentally pushed to the wrong branch
Scenario:
Developer intended to push to:
Plain text
feature/payment
But pushed to:
Plain text
main
Explain:
Stop further changes.
Inspect the commit and branch history.
Determine whether the push was accepted.
Follow the team's branch protection and incident procedure.
Coordinate with the repository maintainers to correct the branch history or create a corrective commit.
Do not automatically reset the shared branch.
Part J – GitHub and remote repository command cheat sheet
17. Important commands for students
Command
Purpose
git remote -v
List configured remotes
git remote add origin URL
Add remote
git remote show origin
Inspect remote details
git clone URL
Clone repository
git push origin main
Push local branch
git push -u origin main
Push and configure upstream
git fetch origin
Download remote updates
git pull origin main
Fetch and integrate changes
git branch -a
List all known branches
git branch -r
List remote-tracking branches
git branch -vv
Display branch tracking details
git switch --track origin/feature
Track remote branch
git remote set-url origin URL
Change remote URL
git fetch upstream
Fetch original repository updates
Important command combinations
Scenario 1: New developer joins the project
Bash
git clone
<
repository-url
>
Scenario 2: Developer uploads a new feature branch
Bash
git switch -c feature/new-feature
git add
.
git commit -m
"Add new feature"
git push -u origin feature/new-feature
Scenario 3: Developer wants to inspect remote changes
Bash
git fetch origin
git log --oneline --graph --all
Scenario 4: Developer wants to synchronize with main
Bash
git switch main
git pull origin main
Scenario 5: Developer wants to update a fork
Bash
git fetch upstream
git switch main
git merge upstream/main
Part K – Assessment
18. Ten MCQs
## Session 3 knowledge test
0/10 answered
1
.
What is GitHub?
A programming language
A Git repository hosting and collaboration platform
An operating system
A database
2
.
What is the default conventional remote name when cloning?
upstream
master
origin
remote
3
.
Which command uploads local commits?
git fetch
git push
git clone
git status
4
.
What does git fetch do?
Automatically merges all changes
Downloads updates without integrating them into the current branch
Deletes remote branches
Creates a GitHub account
5
.
What does git pull normally do?
Fetch and integrate changes
Only display logs
Delete local commits
Create a branch
6
.
What is origin/main?
A GitHub user
A local branch
A remote-tracking branch
A commit message
7
.
What is the purpose of a Pull Request?
Install Git
Request review and integration of proposed changes
Delete commits
Create SSH keys
8
.
What does git clone do?
Only downloads a ZIP file
Creates a local repository from an existing repository
Deletes remote history
Commits changes
9
.
What is an upstream remote commonly used for?
Tracking an original repository from which a fork was created
Storing passwords
Replacing Git
Creating tags
10
.
Why can a push be rejected as non-fast-forward?
Git is not installed
The remote contains commits absent from the local branch
The file is too small
The branch has no name
Submit assessment
19. Interview questions – Real-world scenarios
Ask students to explain their answers and demonstrate commands.
What happens when you execute
git push
?
What is the difference between Git and GitHub?
What is the difference between
git fetch
and
git pull
?
What is the difference between
origin
and
upstream
?
What is a remote-tracking branch?
What is the difference between
git init
and
git clone
?
Why does Git reject a non-fast-forward push?
How do you authenticate Git with GitHub?
What is a Pull Request?
What is branch protection?
How do you troubleshoot an authentication failure?
What happens when two developers push to the same branch?
What is the purpose of an SSH public key?
Why should private keys and access tokens never be committed?
How does GitHub Actions help in a DevOps workflow?
Part L – Final Module Project
20. Build a professional GitHub repository
Portfolio assignment
Students will create a GitHub repository that demonstrates their understanding of Git and GitHub.
Project name:
devops-source-control-project
Suggested structure:
Plain text
devops-source-control-project/
│
├── README.md
│
├── src/
│   ├── app.py
│   └── payment.py
│
├── config/
│   └── application.properties
│
├── docs/
│   └── architecture.md
│
├── tests/
│   └── test_app.py
│
└── .gitignore
Project requirements
Requirement
Expected evidence
Local repository
Git initialization
Version history
Minimum 10 meaningful commits
Branch management
Minimum three feature branches
Merge
Successfully merged features
Conflict resolution
At least one resolved conflict
Rebase
Demonstrate feature branch rebase
Squash
Combine commits
Stash
Demonstrate unfinished work recovery
Reset and revert
Demonstrate both safely
GitHub
Publish remote repository
Collaboration
Create a Pull Request
Documentation
Professional README
README requirements
The README should contain:
Project title.
Business problem.
Project description.
Technologies used.
Repository structure.
Git commands demonstrated.
Branching workflow.
Conflict resolution evidence.
GitHub repository URL.
Screenshots of practical execution.
Students should capture evidence of:
Local Git commit history.
Branching graph.
Merge conflict resolution.
Rebase operation.
GitHub repository.
Pull Request.
Successful merge.
Final clean Git status.
21. Final six-hour module completion
Module 3 – SCM with Git and GitHub
6 hours completed in the training plan
## Session 1 – Git Fundamentals
VCS, Git architecture, installation, configuration, repositories, file lifecycle, commits and .gitignore.
2 hours
## Session 2 – Git Branching and Advanced Operations
Branching strategies, merge, conflict resolution, rebase, squash, stash, reset, restore and revert.
2 hours
## Session 3 – GitHub and Remote Repositories
GitHub, authentication, clone, push, pull, fetch, upstream, Pull Requests and collaboration.
2 hours
Total training duration
6 hours
22. What students should be capable of after this module
Students should independently be able to:
Create and manage Git repositories.
Track and maintain application versions.
Work with feature branches.
Merge changes and resolve conflicts.
Recover from common Git mistakes.
Maintain clean commit history.
Create and manage GitHub repositories.
Collaborate with other developers.
Submit and review Pull Requests.
Understand how GitHub integrates with CI/CD.
Connection to upcoming DevOps modules
Make sure students understand this progression:
Plain text
Source Code (Git)
|
v
Repository Hosting (GitHub)
|
v
CI/CD Automation (Jenkins / GitHub Actions)
|
v
Build (Maven / Gradle)
|
v
Containerization (Docker)
|
v
Deployment (Kubernetes)
|
v
Monitoring and Observability
Git is the foundation for almost every subsequent DevOps module.
23. Trainer's recommendation
For absolute beginners, six hours is enough to introduce Git and GitHub and provide practical exposure to the essential workflows. It is not enough to guarantee independent mastery of every advanced recovery and collaboration scenario.
I recommend giving students one additional self-practice task:
Ask each student to create their own GitHub repository, make a feature branch, push it, create a Pull Request and merge it.
Do not accept a screenshot alone. Ask them to explain what happened internally at every step.
That will tell you whether they genuinely understand Git or have simply memorized commands.
Module 3 teaching material completed
ChatGPT can make mistakes. Check important info.
Latest response
Think
To pick up a draggable item, press the space bar.
While dragging, use the arrow keys to move the item.
Press space again to drop the item in its new position, or press escape to cancel.
To pick up a draggable item, press the space bar.
While dragging, use the arrow keys to move the item.
Press space again to drop the item in its new position, or press escape to cancel.
Response complete

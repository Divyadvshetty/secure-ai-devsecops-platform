
# Day 1 — Introduction to Operating Systems and Linux Architecture

Today's objective: By the end of these two hours, students should understand what an operating system does, what Linux is, how Linux is structured, and how an application interacts with the operating system.

We will not try to teach the entire Linux filesystem or all Linux commands today. Those will be covered separately, one day at a time.

The teaching approach follows your training brief: assume no prior Linux knowledge, explain concepts using analogies, connect them to real DevOps work, and make students execute commands themselves. 

Pasted text(5).txt

## 1. Today's timetable

| Time | Duration | Topic |
| --- | --- | --- |
| 00:00–00:10 | 10 min | Introduction: why do we need an OS? |
| 00:10–00:30 | 20 min | What is an operating system? |
| 00:30–00:55 | 25 min | What is Linux? Kernel vs distribution |
| 00:55–01:15 | 20 min | Linux architecture: hardware, kernel and user space |
| 01:15–01:40 | 25 min | How applications interact with the kernel |
| 01:40–01:50 | 10 min | Live Linux terminal demonstration |
| 01:50–02:00 | 10 min | Revision and interview questions |

# Part 1 — Why do we need an operating system?

00:00–00:10 · 10 minutes

### 1.1 Start with a real-world example

Ask your students:

"Imagine you have purchased a new laptop. It has a processor, 16 GB RAM, a 512 GB SSD and a network card. Can you directly open Chrome, play a video or run Python programs?"

Let them answer.

Explain:

The laptop has hardware, but applications need a way to use that hardware.

For example:

* Chrome needs memory to store its working data.
* A video player needs the CPU to decode video.
* A Python application needs to read files.
* Jenkins needs to execute build processes.
* Docker needs operating-system capabilities to isolate containers.
* A monitoring agent needs to collect CPU and memory information.

Who coordinates all these activities?

The operating system.

### 1.2 Company analogy

Imagine a large organisation:

![Departmentation: Definition, Types, Advantages, and Importance - ParikshaPatr](https://images.openai.com/static-rsc-4/np6RZbONysR1H96sqihlV9eGCuAg9SIUzq8C8OE8XGMTOykRBFT3qOATW3DXuQj7-Bu6_AUxegzCmEd1kXjqB-eAaCCLArZeNR9bWrrffyK-vpTqOH2WttgvEx-ZS0Rkg39GnZh4mjdngTbmjV0dcacuShm4pj7iq4hlSCGni-o?purpose=inline)

[parikshapatr.com](https://parikshapatr.com/solutions/departmentation-in-management-definition-types-advantages-and-importance?utm_source=chatgpt.com)

| Organisation | Computer |
| --- | --- |
| Company infrastructure | Computer hardware |
| Management and coordination | Operating system |
| Employees performing work | Applications |
| Office resources | CPU, RAM, storage |
| Access control | User permissions |
| Work allocation | Process scheduling |

Explain:

If every employee independently tries to use the same company resource without coordination, there will be conflicts.

Similarly, if applications directly controlled the hardware without coordination, resource conflicts and security problems would arise.

The OS provides controlled access to resources.

Trainer question: What would happen if two applications needed CPU time at the same moment?

Expected answer: The operating system schedules CPU time between processes so they can make progress.

# Part 2 — What is an operating system?

00:10–00:30 · 20 minutes

### 2.1 Definition

An operating system is system software that manages computer hardware and provides common services to application programs.

Examples:

* Windows
* Linux
* macOS
* Android
* iOS

### 2.2 Major responsibilities of an operating system

Teach these six responsibilities.

1. Process management

A process is an instance of a running program.

Example: When you open a terminal and run a Python application, Linux creates a process to execute it.

The OS manages process creation, scheduling and termination.

2. Memory management

Applications need RAM to run.

For example:

* Jenkins needs memory to execute jobs.
* Java applications need memory for the JVM and application data.
* Kubernetes workloads running on a Linux node consume memory.

The OS manages memory allocation and virtual memory.

3. Filesystem management

Applications need to store and retrieve information.

Examples:

* Configuration files.
* Application logs.
* Scripts.
* Deployment artifacts.

The OS provides filesystem interfaces and controls access.

4. Device management

The OS coordinates devices using drivers and other kernel components.

Examples:

* Hard disks.
* Network interfaces.
* USB devices.
* Graphics hardware.

5. Security and access control

The OS controls which users and processes can access resources.

For example, a developer should not automatically have permission to modify every system configuration file.

6. Networking

The OS provides networking capabilities that applications use to communicate.

For example, an Nginx server accepts HTTP requests through the Linux networking stack.

### 2.3 Practical DevOps connection

Give students this scenario:

A Jenkins agent is running on an Ubuntu server. A pipeline executes a build, writes logs and uploads an artifact.

Ask: Which OS responsibilities are involved?

| Pipeline activity | OS responsibility |
| --- | --- |
| Execute build process | Process management |
| Allocate memory to build | Memory management |
| Read source code | Filesystem management |
| Write build logs | Filesystem management |
| Connect to Git repository | Networking |
| Access build directory | Security and permissions |

Key lesson: DevOps engineers work with tools such as Jenkins, Docker, Kubernetes and Ansible, but these tools depend on operating-system capabilities.

# Part 3 — What is Linux?

00:30–00:55 · 25 minutes

### 3.1 Explain Linux from the beginning

Linux is an open-source operating-system kernel originally created by Linus Torvalds in 1991.

The kernel is the central component of the operating system. It manages hardware resources and provides services to programs.

A common beginner misunderstanding is:

"Linux means Ubuntu."

Correct this carefully.

Linux and Ubuntu are not the same thing.

* Linux is the kernel.
* Ubuntu is a Linux distribution.
* Ubuntu packages the Linux kernel with utilities, libraries, package management, configuration and other software.

### 3.2 Kernel versus distribution

![What is a Linux Distribution (Distro)? | by Tanishq Arora | Medium](https://images.openai.com/static-rsc-4/NtLKrYUn1-oeUv7rJvCXvLbMEf2xmAWKnYUEAJBj7paUX3vCXVChsAiEhgVUbZAM8h-af4iLCxo24qXehBuZBoJso3zumGPrzXXpqu6HiVMCsc7ovoNN4Nx7x1T_kzzxwJ3btZpKIHhjCJFifoRPZO0PKoS6En5pRQ2CqRGQieg?purpose=inline)

[medium.com](https://medium.com/%40sre-devops-interview/what-is-a-linux-distribution-distro-5027e17ce64b?utm_source=chatgpt.com)

Use this analogy:

Imagine you are building a car.

* Engine = Linux kernel.
* Transmission, electrical systems and supporting components = system utilities and libraries.
* Complete assembled car = Linux distribution.

The engine is essential, but an engine alone is not a complete car.

Similarly, the Linux kernel is essential, but a complete Linux distribution includes many additional components.

### 3.3 Examples of Linux distributions

![各发行版Linux介绍-腾讯云开发者社区-腾讯云](https://images.openai.com/static-rsc-4/36ARFxpNYdh5QKoIg35g_VsM0bJlNc0q6HMox5S8Mhu-gvR1I0Ftc7wP8rWH1mrPZJgtPbOALOTe6dEA3RPhYzrqR_ra_hEaxY9A0mRz0o13gqQrn469ZY3pinDDhnMpgdRmwKW8Owm94j73EaIPTWaWydpYIC7hHc4nnGL1_i4?purpose=inline)

Ubuntu

Commonly used for cloud servers, application hosting and development.

![RHEL, Red Hat Enterprise Linux | Piros](https://images.openai.com/static-rsc-4/EjVvGt3mJ4qjZ_lrzyGgIBMGV35FRC6XLF9_SmD_JC8iKHnIw1VoTOsgi5UzQiLbC6Y2ydH1wd0kGHyxS8COY1Oy5mDpGPgsibK-ZLBOOEW1XD9QYT1sq1DV67rsF6x8egnIwIEpvOrYMi2xabKB6F53vex_wsjYUNROPguFcm0?purpose=inline)

Red Hat Enterprise Linux

Enterprise Linux distribution with commercial support options.

![Software We Use At NixNexus - NixNexus - Your Guide to everything FOSS](https://images.openai.com/static-rsc-4/oQLMZJ5NWzk43EGLhYMslNEVN8F1l_EH4xxV0UNmIrjEA4CfVsV41sJNau6RtUOuvUQIgSmpqY0AuYTVVJt3szz23XQz8rmBqFka5DdSUv8b7LFpDD1S9-4ABn8nvDJONySZWntm5ATShZ9HUpT2VG3GAD71f_XdussdqaEPSGY?purpose=inline)

Debian

Widely used Linux distribution and the base for Ubuntu.

![Rocky Linux Logo PNG Vector, Icon Free Download](https://images.openai.com/static-rsc-4/tv5kzW71JLYaKfCQ1OqLatJLc2lUIJYBuEfiOwQJltrxmTuJKY05i8z2bciRwvJ_gnkILEknxaTNls8NKENouB9_suaj7f0TRbYeyJvy6CzgfgVAbQiNFwxYiGZASBjDf4he9irOaIgbRgKr5YLxHWMKWCopOI1JTk3yr0nL_MM?purpose=inline)

Rocky Linux

Enterprise-compatible Linux distribution.

![Amazon Linux Partners - Amazon Web Services (AWS)](https://images.openai.com/static-rsc-4/wWMZ1JZsXfoszNg9irQWnbfZ-EL4p7UpFxlTiOhtVHelsbdG3hyT8eRySKVwNFtT10flJP8Q9tGBTsBZbkGnVPqSLW19AEoK0NOYIACPrwTxhquivdbkGdwgkHS2HKFDK9eJOOzObRe_Bph8oCAuw616B7fpgSSyqnPOnHSUxLk?purpose=inline)

Amazon Linux

Linux distribution maintained by AWS for its cloud ecosystem.

Other examples include AlmaLinux and SUSE Linux Enterprise.

### 3.4 Why do organisations use different Linux distributions?

Ask students:

"Why doesn't every company use Ubuntu?"

Explain that organisations consider:

* Vendor support.
* Security updates.
* Software compatibility.
* Release lifecycle.
* Existing infrastructure.
* Operational team expertise.
* Compliance requirements.

Example:

A company may use Ubuntu LTS for application servers, RHEL for an enterprise product that requires vendor certification, and Amazon Linux for EC2 workloads.

These choices depend on the organisation's requirements.

### 3.5 Check the Linux environment

Ask students to open their Linux terminal and execute:

Bash

```
cat /etc/os-release
```

Explain:

* `cat` displays file contents.
* `/etc/os-release` contains operating-system identification information.

Representative output:

Plain text

`NAME="Ubuntu"
VERSION="24.04.3 LTS (Noble Numbat)"
ID=ubuntu
ID_LIKE=debian
VERSION_ID="24.04"
PRETTY_NAME="Ubuntu 24.04.3 LTS"`

The exact release will vary according to the machine.

Next:

Bash

```
uname -r
```

This displays the running kernel release.

Example:

Plain text

`6.8.0-xx-generic`

The exact value depends on the installed kernel.

Then:

Bash

```
uname -a
```

This provides additional information, including kernel name, hostname, kernel release, build information and architecture.

Trainer emphasis: `/etc/os-release` tells us about the distribution. `uname` tells us about the running kernel. They answer different questions.

# Part 4 — Linux architecture: hardware, kernel space and user space

00:55–01:15 · 20 minutes

### 4.1 Understand the three main layers

Explain that Linux can be understood using three major layers:

1. Hardware
2. Kernel space
3. User space

![Linux Made Simple: The Ultimate Beginner’s Guide to Essential Usage | by Sami ST | Mar, 2026 | Medium](https://images.openai.com/static-rsc-4/4HKwozSLoAJhJtWk_v3Y7JBoKejgCGR7gEl7QCr5CFog5RRqUHb6p6A3hGq3XpMP1_mJoNPMpnQU7n-GKvjFnUSNTXQ9aJiaiMt4Ej84izpqC4-YchvXDS2-GtGxI-bLE5d0aObq153tTqARBXDVgDhGVWq9b6El8vBlOSYHFjE?purpose=inline)

[samist.medium.com](https://samist.medium.com/linux-made-simple-the-ultimate-beginners-guide-to-essential-usage-bc21cdd6cbad?utm_source=chatgpt.com)

Layer 1: Hardware

Physical resources:

* CPU — executes instructions.
* RAM — stores working data.
* Disk — stores persistent data.
* Network card — communicates with other systems.

Layer 2: Kernel space

The Linux kernel executes in a privileged environment called kernel space.

Its responsibilities include:

* CPU scheduling.
* Memory management.
* Process management.
* Filesystem management.
* Device drivers.
* Network stack.

Layer 3: User space

User space is where ordinary applications and utilities execute.

Examples:

* Bash shell.
* Python.
* Nginx.
* Jenkins agent.
* Docker CLI.
* Monitoring agents.

### 4.2 Kernel space versus user space

This distinction is important for understanding Linux security and troubleshooting.

| Kernel space | User space |
| --- | --- |
| Privileged execution environment | Restricted execution environment |
| Runs kernel code | Runs applications and utilities |
| Manages hardware resources | Requests access to resources |
| A kernel failure can affect the entire system | An application failure usually affects that application or its dependencies |
| Handles system calls | Makes system calls when OS services are needed |

Ask students:

"If a Python application crashes, does the entire Linux kernel necessarily crash?"

Expected answer: No. A normal user-space application crash generally does not crash the kernel.

"Can a faulty kernel driver cause a complete server failure?"

Expected answer: Yes. A serious kernel or driver failure can cause a kernel panic or other system-wide problems.

### 4.3 What happens when a command is executed?

Let's use a simple example.

Bash

```
ls /etc
```

Explain the execution:

1. The user enters `ls /etc` in the terminal.
2. Bash reads and interprets the command.
3. Bash locates the `ls` executable, unless an alias or function changes command resolution.
4. The executable runs in user space.
5. It requests filesystem information through operating-system interfaces.
6. The kernel checks access permissions and coordinates filesystem operations.
7. The program displays the directory entries.
8. The terminal displays the output.

User types: ls /etcTerminal receives inputBash interprets commandBash resolves ls executablels executes in user spaceRequests filesysteminformationKernel checks access andhandles requestFilesystem provides directoryinformationls formats outputTerminal displays output

This is a simplified conceptual flow. Actual implementations can involve multiple library calls, system calls and filesystem operations.

# Part 5 — How applications communicate with the kernel

01:15–01:40 · 25 minutes

### 5.1 What is a system call?

A system call is a controlled interface through which a user-space application requests a service from the kernel.

Use this analogy:

Imagine a bank customer wants to withdraw money.

The customer cannot directly enter the bank vault. They submit a request through an authorised process. The bank verifies the request and performs the operation.

Similarly, an application cannot freely access protected kernel resources. It requests services through system calls.

### 5.2 Common system calls

| System call | Purpose | Example of where it matters |
| --- | --- | --- |
| `openat()` | Opens or accesses a file | Application reads configuration |
| `read()` | Reads data | Application reads a log or file |
| `write()` | Writes data | Application writes a log |
| `close()` | Closes a file descriptor | Application finishes file access |
| `fork()` | Creates a child process | A process creates another process |
| `execve()` | Executes a program by replacing the current process image | A shell launches a program |
| `socket()` | Creates a communication endpoint | Application networking |

Students do not normally type these names as shell commands. They are kernel interfaces used by programs.

### 5.3 Understand user mode and kernel mode

Modern processors provide privilege levels.

At a beginner level, explain two important execution modes:

* User mode: Applications execute with restricted privileges.
* Kernel mode: The kernel executes with privileged access to system resources.

When a program requests a kernel service through a system call, the processor transitions to kernel mode. After the operation, execution returns to user mode.

The purpose is controlled access and isolation.

### 5.4 Production example — application cannot write to a log file

Imagine a Python application tries to write to:

Plain text

`/var/log/myapp/application.log`

But the application receives:

Plain text

`PermissionError: [Errno 13] Permission denied`

Explain the sequence:

1. Python attempts to write to the log file.
2. It makes an operating-system request.
3. The kernel checks the process credentials and filesystem permissions.
4. The access is denied.
5. The application receives an error.

This is not necessarily a Python problem. It may be a Linux ownership or permission issue.

Later sessions will teach how to investigate and fix this correctly.

### 5.5 Optional advanced demonstration: observe system calls

If `strace` is installed, demonstrate how an engineer can observe system calls made by a program.

First check:

Bash

```
command -v strace
```

If it is installed:

Bash

```
strace -e trace=openat,read,write cat /etc/os-release
```

Explain:

* `strace` traces system calls and signals.
* `-e trace=...` filters the system calls being displayed.
* `cat` is the program being traced.
* `/etc/os-release` is the file being read.

Representative output may contain lines resembling:

Plain text

`openat(AT_FDCWD, "/etc/os-release", O_RDONLY) = 3
read(3, "PRETTY_NAME=...", 131072) = 150`

Explain the important parts:

* `openat` represents a file-opening request.
* `O_RDONLY` means read-only access.
* `= 3` means the call returned file descriptor 3.
* `read` reads data from that file descriptor.

Actual output varies by operating-system version, program and environment.

If `strace` is unavailable, do not interrupt the class to install it. Explain the concept and use the demonstration as an optional follow-up lab.

# Part 6 — Live Linux terminal demonstration

01:40–01:50 · 10 minutes

Ask students to execute these commands themselves.

### Demonstration 1 — Identify the OS

Bash

```
cat /etc/os-release
```

Ask: Which Linux distribution is running?

### Demonstration 2 — Identify the kernel

Bash

```
uname -r
```

Ask: Is this the distribution version or the kernel version?

### Demonstration 3 — Identify the CPU architecture

Bash

```
uname -m
```

Possible output:

Plain text

`x86_64`

Explain that this commonly indicates a 64-bit x86 architecture.

### Demonstration 4 — Identify the current user

Bash

```
whoami
```

Ask: Why does the identity of the current user matter when troubleshooting permission errors?

### Demonstration 5 — Inspect running processes

Bash

```
ps -ef | head
```

Explain:

* `ps` displays process information.
* `-e` selects all processes.
* `-f` requests full-format listing.
* `|` sends the output to another command.
* `head` displays the first few lines.

We will study `ps`, pipes and `head` in more detail in later sessions.

### Demonstration 6 — Identify PID 1

Bash

```
ps -p 1 -o pid,comm,args
```

Representative output:

Plain text

`PID COMMAND COMMAND
 1 systemd /sbin/init`

Explain:

* PID means Process ID.
* Process ID 1 is the first userspace process in a typical modern Linux boot.
* On a standard Ubuntu Server installation, it is usually systemd.

This is a useful connection to tomorrow's boot-process lesson.

# Part 7 — Revision and interview questions

01:50–02:00 · 10 minutes

Ask students to answer first, then discuss the answers.

### Beginner questions

1. What is an operating system?

An operating system manages computer hardware and provides common services to applications.

2. What is Linux?

Linux is an open-source kernel used by many operating-system distributions.

3. Is Ubuntu the Linux kernel?

No. Ubuntu is a Linux distribution that includes the Linux kernel and other software.

4. What is the difference between kernel space and user space?

Kernel space is the privileged execution environment for the kernel. User space is the restricted environment where ordinary applications run.

5. What is a process?

A process is an instance of a running program.

### Intermediate questions

6. Why do applications use system calls?

To request operating-system services such as file access, process creation and networking.

7. Why can't an ordinary application directly access all hardware resources?

Because the operating system enforces controlled access, isolation and security.

8. What happens when an application reads a file?

The application requests access through operating-system interfaces. The kernel checks access and coordinates the filesystem operation.

9. What happens if a user-space application crashes?

Normally, that process terminates or fails without necessarily affecting the kernel or other processes.

10. Why should a DevOps engineer understand Linux architecture?

Because DevOps tools and workloads rely on Linux processes, memory, filesystems, networking, security and other OS services.

## Day 1 student assessment

Quick knowledge check

0/5 answered

1. What is Linux?

A Linux distribution

The Linux kernel

A package manager

2. Which layer manages CPU scheduling and memory management?

User space

Terminal

Kernel

3. Where does a normal Python application execute?

User space

Kernel space

BIOS

4. What is a system call?

A Linux distribution

A controlled interface to request kernel services

A terminal emulator

5. Which command shows the running kernel release?

cat /etc/os-release

uname -r

whoami

Submit answers

## Homework before Day 2

Ask students to complete these tasks independently.

1. Explain the difference between an operating system, Linux kernel and Linux distribution.
2. Draw the three-layer Linux architecture: hardware, kernel space and user space.
3. Explain how an application reads a file using a system call.
4. Execute the six terminal demonstrations again and record their outputs.
5. Write a short explanation of why a permission error can originate from the operating system rather than the application.


### 5.1 What is the root filesystem?

In Linux, the root filesystem is the filesystem mounted at `/`.

It contains the directory hierarchy required for the operating system to function.

For example:

Plain text

`/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── proc
├── root
├── run
├── sbin
├── sys
├── tmp
├── usr
└── var`

Explain that the root filesystem is not necessarily the same thing as the physical root disk or partition. It is a filesystem mounted at the path `/`.

A server might have separate filesystems for `/`, `/boot`, `/home` and `/var`.

### 5.2 What does mounting mean?

Mounting means making a filesystem accessible at a directory called a mount point.

Use an analogy:

A storage device is like a filing cabinet. Mounting is like placing that cabinet into an accessible location in an office.

For example, a separate disk may be mounted at:

Plain text

`/data`

Applications can then access its files through `/data`.

We will cover partitions, mount points and `df`, `du`, `lsblk` and `findmnt` in a dedicated storage session.

### 5.3 What happens after the root filesystem is ready?

The kernel starts the initial user-space process.

On a typical modern Ubuntu Server system, that process is `systemd`, with PID 1.

### 5.4 What is PID 1?

PID means Process ID.

Every process running in Linux has a process ID.

PID 1 is the first userspace process started by the kernel in a normal boot sequence.

On modern Ubuntu systems, PID 1 is normally systemd.

Systemd is responsible for bringing the system into its configured operating state and managing services and other units.

![Introduction to systemd | PDF](https://images.openai.com/static-rsc-4/Kq_canMIWF8NY4xLatIKgNXILHvrL8DZPbkRxiH9itNw-sCCViNn2F2e0ntiD-XcHb3TdTbQrdRjhRF5CBk6-2UbBLgvAv2bAMhOkaVIovlR4neCrGxmu1G-NaHQcYP1AnZaWEeXMpFmxKsv4zNN8WaQwgtG4n0PGb5bRwomTxE?purpose=inline)

[slideshare.net](https://www.slideshare.net/slideshow/introduction-to-systemd/40899217?utm_source=chatgpt.com)

### 5.5 What is systemd?

Systemd is a system and service manager used by many modern Linux distributions.

It can:

* Start system services.
* Stop and restart services.
* Manage service dependencies.
* Manage system targets.
* Monitor service state.
* Collect service output through the journal when configured.
* Manage various other unit types.

Examples of services:

* SSH server.
* Nginx.
* Docker.
* Cron.
* Monitoring agents.

### 5.6 How does systemd start services?

Suppose a Linux server needs SSH and Docker after boot.

A simplified example:

Kernel starts systemd (PID 1)systemd reads unitconfigurationsystemd determines defaulttargetChecks unit dependenciesStarts required servicesSSH serviceDocker serviceOther required servicesSystem reaches configuredoperating state

Actual systemd startup is dependency-driven and can start independent units in parallel. The diagram is a simplified teaching representation.



What is a Process?

• Definition: Any instance of a running program, script, or command.
• Lifecycle: Starts when you launch an application or command and ends when the program finishes or is closed.
• Interaction: Often has a user interface or runs in your current terminal shell (foreground or background).
• Examples: A text editor (vim), a web browser (Chrome), a shell script, or a manual ls command.
• Key Attributes: Tracked by the kernel with a unique Process ID (PID), Parent PID (PPID), owner, and resource limits.
• How to view: Using commands like ps, top, or htop.

What is a Service?

• Definition: A specialized background process (or group of processes) that runs continuously to provide a specific service or feature to the operating system or users.
• Lifecycle: Configured to start automatically when the system boots and run continuously until the system shuts down.
• Interaction: Runs without direct user interaction or terminal attachment.
• Examples: Web servers (NGINX, Apache), database servers (MySQL), remote login (sshd), or automated scheduling (cron).
• Management: Controlled by an init system like systemd via commands such as systemctl start, systemctl stop, or systemctl enable.

Similarities

• Under the Hood: Every service is fundamentally a process at its core.
• Kernel Management: The Linux kernel treats both services and normal processes the same way—allocating them a PID, scheduling CPU time, and tracking memory.
• Signals: Both can receive standard Linux process control signals (such as SIGTERM or SIGKILL) to pause, stop, or reload.

Differences


Feature	Process (General)	Service (Daemon)
Primary Purpose	Performs a task requested by a user or temporary script.	Provides continuous, background system or network functionality.
Startup Trigger	Started manually by a user or another application.	Started automatically by an init system (systemd) during boot.
Lifecycle	Transient; ends when the task finishes or the app closes.	Long-running; stays active the entire time the system is on.
User Interaction	Often interactive (GUI or terminal prompts).	Non-interactive background daemon.
Management Tool	Killed/managed via standard process tools (kill, pkill, fg/bg).	Managed via service controllers (systemctl, service).
Examples	bash, python script.py, htop, firefox.	sshd, nginx, mysqld, docker.


### 5.7 Inspect PID 1

Ask students to run:

Bash

```
ps -p 1 -o pid,ppid,comm,args
```

Representative output:

Plain text

`PID PPID COMMAND COMMAND
 1 0 systemd /sbin/init`

Explain:

* `ps` displays process information.
* `-p 1` selects process ID 1.
* `-o` selects the output columns.
* `pid` is the process ID.
* `ppid` is the parent process ID.
* `comm` is the command name.
* `args` shows the command and arguments.

### 5.8 Inspect systemd

Bash

```
systemctl --version
```

This displays the installed systemd version.

Now:

Bash

```
systemctl status
```

This displays a summary of the system's state, including information about units and system activity.

Also run:

Bash

```
systemctl list-units --type=service --state=running
```

This lists running service units.

Important distinction: A service can be running without being enabled for automatic startup. We will examine this in detail in the service-management session.

# Part 6 — systemd targets and service startup

01:25–01:45 · 20 minutes

### 6.1 What is a systemd target?

A systemd target is a unit used to group other units and represent a particular system state.

Think of a target as a predefined destination that the operating system needs to reach.

For example:

* A server may boot into a multi-user command-line environment.
* A desktop may boot into a graphical environment.
* A recovery environment may provide limited functionality for troubleshooting.

### 6.2 Important systemd targets

| Target | Purpose |
| --- | --- |
| `default.target` | Default target selected for normal startup |
| `multi-user.target` | Multi-user, non-graphical system state |
| `graphical.target` | Multi-user system state with graphical login |
| `rescue.target` | Rescue environment with limited services |
| `emergency.target` | Minimal emergency environment |

`default.target` is commonly configured as a symbolic link to another target.

### 6.3 How targets relate to services

![How to set up a customized target on CENTOS](https://images.openai.com/static-rsc-4/oPb-kxMbUPCGHfrKNkJJLOm90MoQyp8YNRlYwnq2hvHbR8f-gD4WWg3BQnNh-rIQNEjoL_tPQoxvd0F7V3vlVJIXPpKc5dWM91zIL4bMUipKyPC9dVMmViuVvC5iUAAYFLJbL4B9-__h8vWUnFw94Ti_mFt2WvgO1lQ5s8O5V0Y?purpose=inline)

[linkedin.com](https://www.linkedin.com/pulse/how-set-up-customized-target-centos-promise-edah-frank?utm_source=chatgpt.com)

For a typical server:

Plain text

`default.target
 |
 v
multi-user.target
 |
 +----> ssh.service
 |
 +----> cron.service
 |
 +----> docker.service
 |
 +----> other required services`

This is a simplified illustration. Actual dependencies are determined by unit configuration, dependencies and ordering relationships.

### 6.4 Inspect the default target

Run:

Bash

```
systemctl get-default
```

Possible output:

Plain text

`multi-user.target`

Explain that this indicates the configured default target, not necessarily every target currently active.

Check active targets:

Bash

```
systemctl list-units --type=target
```

Inspect the default target link:

Bash

```
ls -l /etc/systemd/system/default.target
```

### 6.5 Difference between start and enable

This distinction is very important in DevOps interviews and production operations.

| Command | Meaning |
| --- | --- |
| `systemctl start nginx` | Starts Nginx now |
| `systemctl enable nginx` | Configures Nginx to start automatically through the appropriate boot target |
| `systemctl enable --now nginx` | Enables and starts Nginx |
| `systemctl disable nginx` | Removes the enablement configuration |
| `systemctl stop nginx` | Stops Nginx now |

Production example:

An engineer installs Docker and runs:

Bash

```
sudo systemctl start docker
```

Docker starts successfully.

However, after the next reboot, Docker does not automatically start because the service was not enabled.

The engineer should investigate:

Bash

```
systemctl is-active docker

systemctl is-enabled docker
```

These commands answer two different questions:

* Is the service currently active?
* Is the service configured to start automatically?

Do not enable or disable production services without understanding the operational impact and change-control requirements.

### 6.6 Understand service dependencies

A service may depend on another unit being available.

For example, a network-dependent application service may require networking to be configured before it starts.

Inspect dependencies:

Bash

```
systemctl list-dependencies multi-user.target
```

Inspect a particular service's configuration:

Bash

```
systemctl cat ssh.service
```

The service name can vary by distribution. On Ubuntu, the OpenSSH server unit is commonly `ssh.service`.

# Part 7 — Hands-on lab: investigate the booted Linux server

01:45–01:55 · 10 minutes

Student practical

Scenario: You have joined a DevOps team. Your lead asks you to inspect an Ubuntu server and explain how it booted, which kernel it is running and which services are active.

Students should execute these commands individually.

### Exercise 1 — Identify the boot environment

Bash

```
# Distribution

cat /etc/os-release



# Kernel version

uname -r



# Boot mode

test -d /sys/firmware/efi && echo "UEFI boot" || echo "Legacy BIOS boot"
```

### Exercise 2 — Inspect boot files

Bash

```
# List boot directory

ls -lh /boot



# List kernel images

ls -lh /boot/vmlinuz*



# List initramfs images

ls -lh /boot/initrd.img*
```

### Exercise 3 — Inspect the initial process

Bash

```
ps -p 1 -o pid,ppid,comm,args
```

Ask students to identify PID 1.

### Exercise 4 — Inspect systemd

Bash

```
systemctl --version

systemctl get-default

systemctl status
```

### Exercise 5 — Inspect services

Bash

```
systemctl list-units --type=service --state=running
```

Ask students to identify three running services and explain what they might do.

### Exercise 6 — Inspect the current boot logs

Bash

```
journalctl -b -n 30 --no-pager
```

Explain:

* `journalctl` reads the systemd journal.
* `-b` selects the current boot.
* `-n 30` displays the latest 30 entries.
* `--no-pager` prints directly instead of opening an interactive pager.

### Exercise 7 — Check the time taken to boot

Bash

```
systemd-analyze
```

Representative output:

Plain text

`Startup finished in 4.2s (kernel) + 12.5s (userspace) = 16.7s`

The actual values will vary.

Explain that `systemd-analyze` provides boot performance information. Its output helps distinguish time spent in kernel startup from time spent in userspace startup.

### Exercise 8 — Identify slow services

Bash

```
systemd-analyze blame | head -10
```

This lists units ordered by their recorded startup time, with the slowest entries first.

Important: This is a diagnostic clue, not proof that a service is the cause of a slow boot. Dependencies and parallel startup affect the interpretation.

# Part 8 — Production troubleshooting: server fails to boot

This is an introductory incident walkthrough. Full troubleshooting playbooks will be developed in later classes.

### Scenario

A Linux server was restarted after maintenance. The application is unavailable.

An experienced engineer does not immediately restart the application. First, they identify how far the server progressed through the boot process.

| Symptom | Possible area to investigate |
| --- | --- |
| No firmware startup | Hardware or firmware |
| GRUB menu unavailable | Bootloader or firmware boot entry |
| Kernel panic | Kernel, driver or system configuration |
| Cannot find root filesystem | Storage discovery, initramfs or root device |
| Emergency mode | Filesystem, mount or boot configuration |
| Server boots but SSH is unavailable | Network or SSH service |
| SSH works but application is unavailable | Application service or dependencies |

### Commands to investigate after the server becomes accessible

Bash

```
# 1. Identify the running kernel

uname -r



# 2. Identify the current boot time

uptime -s



# 3. Review current boot logs

journalctl -b -n 100 --no-pager



# 4. Review errors from the current boot

journalctl -b -p err --no-pager



# 5. Review kernel messages

dmesg -T | tail -50



# 6. Identify failed systemd units

systemctl --failed



# 7. Check the default target

systemctl get-default



# 8. Check systemd startup timing

systemd-analyze



# 9. Identify slow-starting units

systemd-analyze blame | head -15



# 10. Inspect the boot filesystem

df -h /boot
```

Explain the investigation:

1. Confirm that the machine is running and identify the kernel.
2. Review boot messages to understand startup problems.
3. Check whether systemd reports failed units.
4. Inspect kernel messages for hardware or driver errors.
5. Review boot timing for unusual delays.
6. Check `/boot` capacity if kernel or boot-file operations have failed.

These commands are for a system that has booted far enough to accept commands. If it cannot boot at all, engineers may need a recovery environment, rescue media or console access.

| Time | Duration | Topic |
| --- | --- | --- |
| 00:00–00:10 | 10 min | Recap and filesystem introduction |
| 00:10–00:30 | 20 min | Linux filesystem architecture |
| 00:30–00:55 | 25 min | Important Linux directories |
| 00:55–01:10 | 15 min | Absolute and relative paths |
| 01:10–01:25 | 15 min | Directory navigation commands |
| 01:25–01:40 | 15 min | Hidden files and symbolic links |
| 01:40–01:55 | 15 min | Hands-on exercises and troubleshooting |
| 01:55–02:00 | 5 min | Revision and homework |

# Part 1 — What is a filesystem?

00:00–00:10 · 10 minutes

### 1.1 Start with a real-world example

Ask students:

"Imagine you have 10,000 documents on your laptop. If all documents were stored in one location without folders, how would you find a particular document?"

Expected answers:

* It would be difficult to find.
* We need folders to organise documents.
* We need a naming convention.
* We need a way to locate information.

Explain:

A filesystem provides a way to organise, store, retrieve and manage files and directories on storage devices.

Linux uses a hierarchical filesystem structure.

A filesystem helps the operating system and applications:

* Organise files.
* Locate files.
* Store data.
* Maintain metadata.
* Control access through permissions.
* Manage storage space.

### 1.2 Office filing cabinet analogy

![О проекте | Виталий Воробьев](https://images.openai.com/static-rsc-4/EANbzePLhfZ5wO9Wekyusj_ktgkiK7cBOl282FmIAkuMnjTf6Qy6ex6Q_hPmxUssYsoLuRPeBA4SrUije5DCcMFSjzE2iff5k_kE1K1crxL3buYbCLo1YaJ00iQv2tcQH0X-jMxszUvqLtblp9Jt4RLDRnrPBZn2dg57M1p7o0g?purpose=inline)

[vorobeoffai.ru](https://vorobeoffai.ru/about/?utm_source=chatgpt.com)

| Office example | Linux filesystem |
| --- | --- |
| Entire office filing system | Root directory `/` |
| Department | Directory |
| Individual document | File |
| Document location | File path |
| Document access rules | File permissions |
| Shortcut to another document | Symbolic link |

For example:

Plain text

`Company
 |
 +-- HR
 | +-- employees.txt
 |
 +-- Finance
 | +-- expenses.xlsx
 |
 +-- IT
 +-- servers.txt`

Linux organises files in a similar hierarchical manner.

### 1.3 Important distinction: filesystem versus directory

A filesystem is the structure and mechanism used to store and retrieve data.

A directory is an organisational structure within a filesystem that holds entries referring to files and other directories.

Do not confuse the two.

For example:

* ext4 is a filesystem type.
* `/etc` is a directory.
* `/etc/ssh/sshd_config` is a file path.

Common Linux filesystem types include:

* ext4
* XFS
* Btrfs
* tmpfs
* vfat

We will study filesystem types, partitions and mounting in a separate storage lesson.

# Part 2 — Linux filesystem architecture

00:10–00:30 · 20 minutes

### 2.1 Why does Linux start with `/`?

In Windows, students may be familiar with:

Plain text

`C:\
D:\
E:\`

Linux follows a different model.

Linux uses a single directory tree beginning at `/`, known as the root directory.

![Day 3: Understanding the Linux Filesystem | by Karthick Dk | devsecops-community | Medium](https://images.openai.com/static-rsc-4/WA3TyRP6yCkrR055eOskQQKbmDjFaJRzrV--HPW5U7-Ib_Xa2fC2hd9IwPbW08IQ8088kw0ol4AmgJLnG52SwuFxXHZxnBec5WmSmjAvkS3q7F_fQx1BXhJyvMVxRnev3MpHrJmxEEEY66SiFBAp3Ws5MGf3K0d7MN-U4KlN8dQ?purpose=inline)

[medium.com](https://medium.com/devsecops-community/day-3-understanding-the-linux-filesystem-072cd9a4089f?utm_source=chatgpt.com)

Explain:

* `/` is the top of the directory hierarchy.
* Every ordinary absolute path starts from `/`.
* Additional filesystems can be mounted at directories within this hierarchy.
* Different physical disks can contribute storage to the same directory tree.

For example:

Plain text

`/
├── etc
├── home
├── var
└── data`

`/data` might be a separate disk mounted there, but it still appears as part of the same directory hierarchy.

### 2.2 How a Linux filesystem is organised internally

At a beginner level, introduce three concepts:

1. Data blocks — store file contents.
2. Inodes — store metadata about files and directories.
3. Directory entries — associate filenames with inode numbers.

![Inode data structure in Linux: The idea behind Hard links and Soft links | by Arshanshaik | Medium](https://images.openai.com/static-rsc-4/tptJm9QsZYFAAyMT-Sbq-GG5U4rqif-aX59Eu0l-6S0NO7hQGcrxjzCJzhL-Ig3el_QXbPWTSVamHF0vJpLRn_S9YglTRZxO3IH0MdxclfYjyL10p9vw7QQB2khfFfx5DeJOIrsio1Ofl0Rt6VXRoOUP7my35AkudyuGUq3DFO8?purpose=inline)

[medium.com](https://medium.com/%40arshanshaik1199/inode-data-structure-in-linux-the-idea-behind-hard-links-and-soft-links-c568b2c08085?utm_source=chatgpt.com)

Explain using an example:

Suppose you create:

Plain text

`/home/student/report.txt`

The filesystem maintains information about:

* The filename `report.txt`.
* The inode associated with that file.
* Metadata such as ownership, permissions, timestamps and size.
* The data blocks containing its contents.

Important: A filename is not stored inside the inode. The directory entry associates the name with the inode.

### 2.3 Demonstrate inode information

Ask students to execute:

Bash

```
touch report.txt



ls -li report.txt
```

Representative output:

Plain text

`1234567 -rw-r--r-- 1 student student 0 Nov 3 10:00 report.txt`

Explain:

| Output | Meaning |
| --- | --- |
| `1234567` | Inode number |
| `-rw-r--r--` | File type and permissions |
| `1` | Hard-link count |
| `student` | Owner |
| `student` | Group |
| `0` | File size |
| `report.txt` | Filename |

The inode number and metadata vary by system.

Ask students:

"If I rename `report.txt` to `report-old.txt`, must the file's contents be copied?"

Expected answer: No. A rename within the same filesystem normally changes directory-entry information rather than copying all file contents.

### 2.4 What is a mount point?

A mount point is a directory where a filesystem is attached to the existing directory tree.

For example:

Plain text

`/data`

A separate disk might be mounted at `/data`.

This allows an application to access the storage using:

Bash

```
cd /data
```

The application does not need to know the physical disk's device name to use the mounted directory.

Trainer emphasis: Linux does not require a separate drive letter for every disk. It can attach multiple filesystems to one directory hierarchy.

# Part 3 — Important Linux directories and their production usage

00:30–00:55 · 25 minutes

This is one of the most important topics for a DevOps engineer. When a server has a problem, knowing where configuration, logs, application files and runtime information are stored helps narrow down the investigation.

### 3.1 The important directories

![Medium](https://images.openai.com/static-rsc-4/yg2d-PB2fTbiAv3tuBTLU3DC6x6IU4W50uCLJpfvpES02XOBtCtj1nHj_TTkWZJhCTpQKMNXnBM6QvqDnqvCO-4YxM6EsREvonDei2IlfSkYGU74X6_xpOY6dh7tQdYozIRf5bKqjYNqLf2rc5-Z_d1uVufDi9mOqC6RfO93_J8?purpose=inline)

[medium.com](https://medium.com/%400xMuhammet/en-tr-linux-file-system-essential-commands-d77caaed1d07?utm_source=chatgpt.com)

| Directory | Purpose | Production example |
| --- | --- | --- |
| `/` | Root of the directory hierarchy | Starting point for all absolute paths |
| `/boot` | Kernel and boot-related files | Kernel and initramfs investigation |
| `/etc` | System-wide configuration | SSH, Nginx and system configuration |
| `/home` | Regular users' home directories | Developer files and SSH client configuration |
| `/root` | Root user's home directory | Administrator's personal files |
| `/var` | Variable application and system data | Logs, caches and application state |
| `/usr` | User-space programs, libraries and resources | Installed commands and applications |
| `/opt` | Optional or third-party software | Manually installed enterprise software |
| `/tmp` | Temporary files | Temporary application and lab files |
| `/var/tmp` | Temporary files intended to persist longer | Longer-lived temporary data |
| `/dev` | Device files | Disk and terminal device interfaces |
| `/proc` | Virtual filesystem for process and kernel information | CPU, memory and process investigation |
| `/sys` | Virtual filesystem exposing kernel and device information | Hardware and device investigation |
| `/run` | Volatile runtime data since boot | Runtime sockets and PID files |
| `/mnt` | Common manual mount location | Temporary storage mount |
| `/media` | Common removable-media mount location | USB storage |

### 3.2 `/etc` — configuration files

Explain:

`/etc` contains system-wide configuration files.

When an application or service starts, it may read configuration from this directory.

Examples:

Plain text

`/etc/ssh/sshd_config
/etc/hosts
/etc/fstab
/etc/passwd
/etc/group`

Demonstration:

Bash

```
ls -l /etc

ls -l /etc/ssh
```

Production scenario:

An administrator changes the SSH server configuration and users can no longer connect.

Where should the administrator investigate?

Bash

```
sudo sshd -t
```

This checks the SSH daemon configuration syntax on systems with OpenSSH server installed.

Important: Do not edit production configuration files during a classroom demonstration. Inspect them and use a disposable lab for modifications.

### 3.3 `/var` — logs and changing application data

This is particularly important in production troubleshooting.

Common locations:

Plain text

`/var/log
/var/cache
/var/lib
/var/tmp`

Explain:

* `/var/log` — system and application logs.
* `/var/cache` — cached data.
* `/var/lib` — persistent application state.
* `/var/tmp` — temporary files that can survive longer than files in `/tmp`.

Demonstration:

Bash

```
ls -l /var

ls -l /var/log
```

Check the total size:

Bash

```
sudo du -sh /var/log
```

Production scenario:

A Linux server reports that its root filesystem is 95% full.

The engineer investigates `/var/log` to determine whether logs are contributing to the problem.

Do not tell students to delete log files immediately. They must identify the source, check log rotation and follow retention requirements.

### 3.4 `/usr` — installed programs and resources

Explain:

`/usr` contains much of the user-space software installed on a Linux system.

Important subdirectories:

| Directory | Purpose |
| --- | --- |
| `/usr/bin` | Many user commands |
| `/usr/sbin` | Many administration commands |
| `/usr/lib` | Libraries |
| `/usr/share` | Architecture-independent shared data |
| `/usr/local` | Locally installed software and resources |

Demonstration:

Bash

```
ls /usr

ls /usr/bin | head

ls /usr/sbin | head
```

Explain that `/usr/local` is commonly used for software installed locally by administrators rather than managed directly by the distribution package manager.

### 3.5 `/proc` — live process and kernel information

Explain:

`/proc` is a virtual filesystem. Its contents are generated by the kernel and represent current system and process information.

Demonstrate:

Bash

```
cat /proc/version
```

CPU information:

Bash

```
head /proc/cpuinfo
```

Memory information:

Bash

```
head /proc/meminfo
```

Process information for PID 1:

Bash

```
ls /proc/1
```

Production relevance:

When investigating a Linux server, engineers can use `/proc` to inspect process and system information without relying only on external monitoring tools.

### 3.6 `/sys` — device and kernel information

Explain:

`/sys` exposes information about devices, drivers and kernel subsystems.

Demonstrate:

Bash

```
ls /sys

ls /sys/class

ls /sys/block
```

Distinguish:

* `/proc` mainly exposes process and kernel-related information.
* `/sys` mainly exposes device and kernel-object information.

Both are virtual filesystems, not ordinary collections of files stored on disk.

### 3.7 `/dev` — device files

Explain:

Linux represents many devices through special filesystem entries.

Examples:

Plain text

`/dev/sda
/dev/sda1
/dev/null
/dev/zero
/dev/tty`

Device names vary depending on hardware and virtualisation.

Demonstrate:

Bash

```
ls -l /dev/null

ls -l /dev/tty
```

Explain that `/dev/null` is a special device that discards data written to it. We will use it later when learning output redirection.

### 3.8 `/run` — runtime information

Explain:

`/run` contains volatile runtime information. It is generally cleared and recreated during boot.

It may contain:

* Service sockets.
* Runtime directories.
* PID files.
* Other temporary state.

Demonstrate:

Bash

```
ls -l /run
```

Production relevance:

A service may use a Unix-domain socket under `/run` to communicate with another process.

### 3.9 `/tmp` — temporary files

Explain:

`/tmp` is used for temporary files.

Create a practice file:

Bash

```
touch /tmp/linux-training-test.txt



ls -l /tmp/linux-training-test.txt
```

Explain that temporary-file cleanup policies vary. Do not assume all files in `/tmp` are removed immediately or only at reboot.

Trainer question: Should an application store its permanent database in `/tmp`?

Expected answer: No. Temporary storage is not appropriate for persistent application data.

# Part 4 — Absolute paths and relative paths

00:55–01:10 · 15 minutes

### 4.1 What is an absolute path?

An absolute path specifies the complete location starting from the root directory `/`.

Example:

Plain text

`/etc/ssh/sshd_config`

Regardless of the current directory, this path identifies the same location.

Demonstrate:

Bash

```
cd /

cd /etc

pwd
```

### 4.2 What is a relative path?

A relative path is interpreted from the current working directory.

Suppose the current directory is:

Plain text

`/home/student/linux-training`

The command:

Bash

```
cd session-01
```

moves to:

Plain text

`/home/student/linux-training/session-01`

The path is relative because it does not start with `/`.

### 4.3 Important path symbols

| Symbol | Meaning | Example |
| --- | --- | --- |
| `/` | Root directory | `cd /` |
| `.` | Current directory | `ls .` |
| `..` | Parent directory | `cd ..` |
| `~` | Current user's home directory | `cd ~` |
| `-` | Previous working directory with `cd` | `cd -` |

### 4.4 Demonstrate step by step

Ask students to execute each command and predict the resulting directory before pressing Enter.

Bash

```
pwd
```

Shows the current working directory.

Bash

```
cd ~

pwd
```

Moves to the current user's home directory.

Bash

```
cd ..

pwd
```

Moves one directory level up.

Bash

```
cd /

pwd
```

Moves to the root directory.

Bash

```
cd /var/log

pwd
```

Moves to `/var/log`.

Bash

```
cd -

pwd
```

Returns to the previous working directory.

### 4.5 Production example

Imagine a deployment script contains:

Bash

```
cd /opt/myapp

./deploy.sh
```

This uses an absolute path to locate the application directory.

If the script instead uses:

Bash

```
cd myapp
```

the command depends on the script's current working directory.

This can cause problems when the script is executed by Jenkins, systemd or a scheduled job because those environments may start in a different directory than the developer expects.

DevOps lesson: Understand the working directory before troubleshooting a script that cannot locate a file.

# Part 5 — Directory navigation commands

01:10–01:25 · 15 minutes

Today we will focus on the commands needed to navigate and inspect directories. Detailed file-inspection commands will come in a later class.

### 5.1 `pwd` — print working directory

Purpose: Displays the current working directory.

Bash

```
pwd
```

Example output:

Plain text

`/home/student`

### 5.2 `ls` — list directory contents

Basic command:

Bash

```
ls
```

Useful options:

| Command | Purpose |
| --- | --- |
| `ls -l` | Long listing |
| `ls -a` | Include hidden entries |
| `ls -h` | Human-readable sizes when used with size output |
| `ls -lh` | Long listing with human-readable sizes |
| `ls -la` | Long listing including hidden entries |
| `ls -ld /etc` | Show information about the directory itself |
| `ls -R` | Recursive listing |

Demonstrate:

Bash

```
ls -l /etc

ls -lah /var/log

ls -ld /home
```

Explain the difference between:

Bash

```
ls -l /etc
```

and:

Bash

```
ls -ld /etc
```

The first lists the contents of `/etc`. The second displays information about `/etc` itself.

### 5.3 `cd` — change directory

Examples:

Bash

```
cd /

cd /etc

cd /var/log

cd ~

cd ..

cd -
```

Explain that `cd` is a Bash built-in, not normally a separate executable.

Why?

Because changing the current working directory must change the shell's own state. An external child process cannot change its parent shell's working directory.

### 5.4 `mkdir` — create directories

Create one directory:

Bash

```
mkdir training
```

Create nested directories:

Bash

```
mkdir -p training/linux/day3
```

Explain:

* `mkdir` creates directories.
* `-p` creates parent directories as needed.
* `-p` also avoids an error if the target directory already exists.

### 5.5 `rmdir` — remove empty directories

Bash

```
mkdir empty-lab

rmdir empty-lab
```

Explain that `rmdir` removes empty directories. It does not remove a directory containing files.

Do not introduce recursive deletion commands as a beginner exercise today.

### 5.6 Live navigation exercise

Ask students to perform the following without copying the next command until they have predicted the result:

Bash

```
pwd

mkdir -p ~/linux-training/day3

cd ~/linux-training/day3

pwd

mkdir config logs scripts

ls -l

cd ..

pwd

ls -la
```

Expected result: A `day3` directory containing three subdirectories: `config`, `logs` and `scripts`.

# Part 6 — Hidden files and symbolic links

01:25–01:40 · 15 minutes

### 6.1 What are hidden files?

In Linux, filenames beginning with a dot (`.`) are treated as hidden by standard directory-listing commands unless hidden entries are requested.

Examples:

Plain text

`.bashrc
.profile
.ssh
.gitignore
.env`

Explain their importance:

| File or directory | Purpose |
| --- | --- |
| `.bashrc` | Bash interactive shell configuration |
| `.profile` | User login environment configuration |
| `.ssh` | SSH client configuration and key files |
| `.gitignore` | Specifies files Git should ignore |
| `.env` | Common application environment-variable file |

A hidden file is not automatically protected or encrypted. Permissions still determine who can access it.

### 6.2 Demonstrate hidden files

Bash

```
cd ~/linux-training/day3



touch normal.txt

touch .hidden-config



# Normal listing

ls



# Include hidden entries

ls -a



# Detailed listing including hidden entries

ls -la
```

Ask:

"Why does `ls` not show `.hidden-config` by default?"

Expected answer: Standard `ls` hides entries whose names begin with a dot unless `-a` is specified.

### 6.3 What is a symbolic link?

A symbolic link, also called a soft link, is a filesystem object that points to another path.

Think of it as a shortcut or signboard pointing to a destination.

![PPT - UNIX File System Layout PowerPoint Presentation, free download - ID:6448335](https://images.openai.com/static-rsc-4/ctNtsC_eHLD33MLn6J29wg0LwghracQMjywdYTsddW0bitZb6IeyFzIXxTxLoAB5_zCJBDNtsyALYg9Lm3N21_I-PR79mOETfOszYAgAunRuFeAt19BbuEV8qA_vhoElOoH6kdZhrCKmPbhLqfv7_Ov2ndWaoGPAIGau5HQhXWM?purpose=inline)

[slideserve.com](https://www.slideserve.com/alec-delaney/unix-file-system-layout?utm_source=chatgpt.com)

Example:

Plain text

`/home/student/app.conf
 |
 v
/etc/myapp/app.conf`

The symbolic link refers to the target path. It does not contain a second copy of the target file's content.

### 6.4 Create a symbolic link

Create a lab directory:

Bash

```
cd ~/linux-training/day3



mkdir -p config

echo "Application configuration" > config/app.conf
```

Create a symbolic link:

Bash

```
ln -s config/app.conf app-config-link
```

Inspect it:

Bash

```
ls -l app-config-link
```

Representative output:

Plain text

`app-config-link -> config/app.conf`

Read through the link:

Bash

```
cat app-config-link
```

Resolve the target:

Bash

```
readlink app-config-link
```

For the absolute resolved path:

Bash

```
readlink -f app-config-link
```

### 6.5 What happens if the target is removed?

In the lab, rename the target:

Bash

```
mv config/app.conf config/app-old.conf
```

Now try:

Bash

```
cat app-config-link
```

The link is broken because its target path no longer exists.

Explain:

A symbolic link can point to a file that is missing. This is called a dangling or broken symbolic link.

Restore the original filename:

Bash

```
mv config/app-old.conf config/app.conf
```

Try again:

Bash

```
cat app-config-link
```

### 6.6 Production example

Imagine an application uses:

Plain text

`/opt/myapp/current`

The directory is a symbolic link to a particular release:

Plain text

`/opt/myapp/current -> /opt/myapp/releases/2026-11-03`

During deployment, the release target may be changed to point to a newer version.

This approach can help with controlled application releases and rollbacks.

Trainer caution: Symbolic links can break when their target is moved or deleted. Always inspect the link and its target during troubleshooting.

# Part 7 — Hands-on student lab

01:40–01:55 · 15 minutes

Practical exercise

Scenario: You have joined a DevOps team. Your lead asks you to create a basic application directory structure, inspect the Linux filesystem and create a symbolic link to an application configuration file.

All exercises use the student's home directory. No root privileges should be required.

### Exercise A — Identify important directories

Execute:

Bash

```
ls -ld /

ls -ld /etc

ls -ld /var

ls -ld /usr

ls -ld /home

ls -ld /tmp

ls -ld /proc

ls -ld /sys
```

Students must explain the purpose of each directory.

### Exercise B — Create an application structure

Bash

```
mkdir -p ~/linux-training/day3/myapp/{bin,config,logs,data,scripts}
```

Create sample files:

Bash

```
touch ~/linux-training/day3/myapp/config/app.conf

touch ~/linux-training/day3/myapp/logs/app.log

touch ~/linux-training/day3/myapp/scripts/start.sh
```

Inspect the structure:

Bash

```
ls -la ~/linux-training/day3/myapp

ls -la ~/linux-training/day3/myapp/config
```

Expected structure:

Plain text

`myapp/
├── bin/
├── config/
│ └── app.conf
├── data/
├── logs/
│ └── app.log
└── scripts/
 └── start.sh`

Ask students to explain why an application might separate configuration, logs, data and scripts.

### Exercise C — Create and inspect a symbolic link

Bash

```
cd ~/linux-training/day3/myapp



ln -s config/app.conf application-config



ls -l application-config

readlink application-config

cat application-config
```

Questions:

1. What is the source file?
2. What is the symbolic link?
3. Does the link contain a copy of the configuration?
4. What happens if the target file is moved?

### Exercise D — Find hidden files

Bash

```
cd ~/linux-training/day3



touch .student-config

touch student-notes.txt



ls

ls -a

ls -la
```

Ask students to explain why the output changes.

### Exercise E — Practise navigation

Bash

```
cd /

pwd



cd /etc

pwd



cd ..

pwd



cd ~

pwd



cd ~/linux-training/day3

pwd
```

Students should be able to explain the current working directory after every command.

# Part 8 — Production troubleshooting scenarios

These are introductory scenarios to connect today's filesystem concepts with real DevOps work.

### Scenario 1: Application cannot find its configuration

Problem:

A deployment script reports:

Plain text

`Configuration file not found: /opt/myapp/config/app.conf`

Ask students what they should investigate before changing anything.

Try:

Bash

```
pwd

ls -ld /opt

ls -ld /opt/myapp

ls -l /opt/myapp/config

find /opt/myapp -type f -name 'app.conf'
```

If the path exists, inspect it:

Bash

```
stat /opt/myapp/config/app.conf

readlink /opt/myapp/config/app.conf

readlink -f /opt/myapp/config/app.conf
```

Explain:

* `pwd` identifies the current working directory.
* `ls -ld` checks individual directories.
* `find` searches for the expected filename.
* `stat` displays file metadata.
* `readlink` checks whether a path is a symbolic link.

Possible causes:

* Wrong file path.
* Incorrect deployment directory.
* Missing configuration file.
* Broken symbolic link.
* Different working directory in the execution environment.

### Scenario 2: Root filesystem is running out of space

Problem:

The monitoring team reports that the root filesystem is 95% full.

Introduce these commands:

Bash

```
df -h

df -i

du -sh /var

du -sh /var/log

du -sh /var/cache

du -h --max-depth=1 /var 2>/dev/null
```

Explain:

| Command | What it investigates |
| --- | --- |
| `df -h` | Filesystem capacity and usage |
| `df -i` | Inode usage |
| `du -sh /var` | Total space used by `/var` |
| `du -sh /var/log` | Space used by logs |
| `du -sh /var/cache` | Space used by caches |
| `du -h --max-depth=1 /var` | Space usage by immediate subdirectories |

Important: `df` and `du` answer different questions. `df` reports filesystem usage, while `du` estimates usage from directory entries it can traverse. Their results can differ, for example when deleted files are still held open by processes.

Do not delete production files without identifying their owner, purpose and retention requirements.

### Scenario 3: A symbolic link is broken

Problem:

A deployment uses:

Plain text

`/opt/myapp/current`

But the application cannot find its files.

Investigate:

Bash

```
ls -l /opt/myapp/current

readlink /opt/myapp/current

readlink -f /opt/myapp/current

ls -ld /opt/myapp
```

Explain that the link may exist while its target is missing.

The correct fix is to identify the intended release and restore the correct target, following the deployment process. Do not replace a production symlink with an arbitrary directory.

# Part 9 — Day 3 knowledge check

Test your understanding

0/5 answered

1. What is the root directory in Linux?

/root

/home

/

2. Where are system-wide configuration files commonly stored?

/etc

/tmp

/proc

3. Which directory commonly stores system and application logs?

/boot

/var/log

/dev

4. What does a relative path depend on?

Current working directory

Kernel version

CPU architecture

5. What does a symbolic link do?

Copies a file

Points to another path

Encrypts a file

Submit answers

# Day 3 homework

1. Draw the Linux filesystem hierarchy and explain at least 15 directories.
2. Explain the difference between a filesystem, directory, file and inode.
3. Practise 10 absolute paths and 10 relative paths.
4. Create a sample application directory with `bin`, `config`, `logs`, `data` and `scripts`.
5. Create a symbolic link and demonstrate what happens when its target is moved.
6. Explain the difference between `/etc`, `/var`, `/usr`, `/proc` and `/sys`.
7. Explain why `df -h` and `du -sh` can show different results.

Production assignment: Imagine an application running on an Ubuntu server cannot find its configuration file, and `/var` is consuming too much storage. Write down the first five investigation steps for each problem.

## Training progress

## Linux fundamentals

Day 1

Operating systems and Linux architecture

Covered

Day 2

Linux boot process and system initialisation

Covered

Day 3

Filesystem hierarchy and directory navigation

Covered

Next: Day 4 — Essential Linux commands: `ls`, `cat`, `touch`, `cp`, `mv`, `rm`, `file`, `stat` and file inspection.

We will focus on how DevOps engineers inspect, create, copy, move and manage files safely, with practical examples and troubleshooting.

#### You said:

day 4

#### ChatGPT said:

# Day 4 — Essential Linux Commands: File and Directory Management

Day 4

2 hours

Beginner level

Today's objective: Learn how to create, inspect, copy, move, rename and remove files and directories in Linux. Students will practise commands commonly used by DevOps engineers while working with application deployments, configuration files, logs and scripts.

Connection to previous days:

* Day 1: Linux operating system and architecture.
* Day 2: Linux boot process and system initialisation.
* Day 3: Filesystem hierarchy, paths and directory navigation.
* Day 4: Working with files and directories using Linux commands.

By the end of this class, students should be able to perform basic file-management operations confidently and understand the risks of modifying files on production servers.

## 1. Today's timetable

| Time | Duration | Topic |
| --- | --- | --- |
| 00:00–00:10 | 10 min | Recap and introduction |
| 00:10–00:25 | 15 min | Understanding Linux commands |
| 00:25–00:45 | 20 min | Creating files and directories |
| 00:45–01:05 | 20 min | Reading and inspecting files |
| 01:05–01:25 | 20 min | Copying, moving and renaming |
| 01:25–01:40 | 15 min | Removing files and directories safely |
| 01:40–01:55 | 15 min | Practical DevOps scenarios |
| 01:55–02:00 | 5 min | Revision and homework |

# Part 1 — Understanding Linux commands

00:00–00:10 · 10 minutes

### 1.1 What is a Linux command?

A Linux command is an instruction given to the shell to perform an operation.

Examples:

Bash

```
pwd

ls

mkdir

touch

cp

mv

rm

cat
```

When a user enters a command in Bash, the shell interprets it and determines how to execute it.

For example:

Bash

```
ls -l /etc
```

Break this command into parts:

| Component | Meaning |
| --- | --- |
| `ls` | Command name |
| `-l` | Option requesting long-format output |
| `/etc` | Argument specifying the target directory |

Explain the difference:

* Command: What operation should be performed?
* Option: How should the operation behave?
* Argument: On which file, directory or object should it operate?

### 1.2 Built-in commands versus external commands

This connects directly to Day 1's shell lesson.

Some commands are built into Bash.

Examples:

Bash

```
cd

pwd

echo

alias

export
```

Other commands are external executable programs.

Examples:

Bash

```
ls

cp

mv

mkdir

cat
```

Students can investigate using:

Bash

```
type cd

type ls

type pwd

type cp
```

Representative output:

Plain text

`cd is a shell builtin
ls is aliased to ...
pwd is a shell builtin
cp is /usr/bin/cp`

The exact output depends on shell configuration and distribution.

Explain:

* `type` helps identify how Bash resolves a command.
* An external command is generally an executable file.
* A built-in command is implemented inside the shell itself.

### 1.3 How do we get help?

Linux commands commonly provide manual pages.

Bash

```
man ls
```

Other useful options:

Bash

```
ls --help

cp --help

mkdir --help
```

Explain:

* `man` opens the manual page.
* `--help` generally displays a short usage summary.
* Press `q` to exit a manual page.

Trainer demonstration: Ask students to look up the meaning of `-r` and `-f` for a command, rather than memorising options without understanding them.

# Part 2 — Creating files and directories

00:10–00:45 · 35 minutes

## 2.1 `mkdir` — create directories

Syntax:

Bash

```
mkdir [OPTIONS] DIRECTORY
```

Create a directory:

Bash

```
mkdir project
```

Verify:

Bash

```
ls -ld project
```

Create nested directories:

Bash

```
mkdir -p project/devops/linux
```

Explain `-p`:

* Creates missing parent directories.
* Does not fail merely because the target directory already exists.

Create multiple directories:

Bash

```
mkdir logs config scripts
```

Create a nested application structure:

Bash

```
mkdir -p myapp/{bin,config,logs,data,scripts}
```

Explain brace expansion:

Bash expands the expression into multiple directory names before executing `mkdir`.

It is a shell feature, not a special feature of `mkdir`.

Verify:

Bash

```
ls -R myapp
```

Expected structure:

Plain text

`myapp:
bin
config
data
logs
scripts`

## 2.2 `touch` — create empty files and update timestamps

Syntax:

Bash

```
touch FILENAME
```

Create an empty file:

Bash

```
touch app.log
```

Create multiple files:

Bash

```
touch app.log error.log access.log
```

Create a configuration file:

Bash

```
touch app.conf
```

Verify:

Bash

```
ls -l
```

Explain:

`touch` can:

* Create an empty file if it does not exist.
* Update access and modification timestamps on an existing file, subject to permissions and options.

Important: `touch` does not erase the existing content of a file.

Demonstrate:

Bash

```
echo "Application started" > app.log



touch app.log



cat app.log
```

Expected output:

Plain text

`Application started`

Explain that the timestamp changes, but the content remains.

## 2.3 `echo` — display or write text

Syntax:

Bash

```
echo "TEXT"
```

Example:

Bash

```
echo "Hello Linux"
```

Output:

Plain text

`Hello Linux`

Write text to a file:

Bash

```
echo "Application configuration" > app.conf
```

Append text:

Bash

```
echo "PORT=8080" >> app.conf
```

Inspect:

Bash

```
cat app.conf
```

Expected output:

Plain text

`Application configuration
PORT=8080`

Explain the difference:

| Operator | Meaning |
| --- | --- |
| `>` | Redirects output and replaces existing file content |
| `>>` | Redirects output and appends to existing file content |

Important production warning

The following command can erase existing file content:

Bash

```
echo "new configuration" > app.conf
```

Never use `>` on a production configuration file unless replacing its contents is intentional.

## 2.4 `file` — identify file type

Syntax:

Bash

```
file FILENAME
```

Examples:

Bash

```
file app.conf

file /bin/ls

file /etc/passwd
```

Representative output:

Plain text

`app.conf: ASCII text
/bin/ls: ELF 64-bit LSB pie executable ...
/etc/passwd: ASCII text`

Explain:

Linux does not determine a file's actual type only from its extension.

For example, a file named:

Plain text

`application.txt`

could contain executable binary data.

The `file` command examines file contents and other information to identify the type.

## 2.5 `stat` — inspect file metadata

Syntax:

Bash

```
stat FILENAME
```

Example:

Bash

```
stat app.conf
```

Representative output:

Plain text

`File: app.conf
 Size: 53
 Blocks: 8
 IO Block: 4096 regular file
Device: ...
Inode: ...
Links: 1
Access: (0644/-rw-r--r--)
Uid: (...)
Gid: (...)
Access: 2026-11-03 ...
Modify: 2026-11-03 ...
Change: 2026-11-03 ...
 Birth: ...`

Explain the important fields:

| Field | Meaning |
| --- | --- |
| File | Name/path |
| Size | Logical file size in bytes |
| Inode | Filesystem inode number |
| Links | Hard-link count |
| Access | File permissions |
| Uid | Owner user ID |
| Gid | Owner group ID |
| Access time | Last access timestamp |
| Modify time | Last content modification timestamp |
| Change time | Last inode metadata change timestamp |

Important distinction: `ctime` means inode change time, not creation time. The `Birth` field may not be supported by every filesystem.

### 2.6 Trainer demonstration — build an application structure

Ask students to create:

Bash

```
mkdir -p ~/linux-training/day4/myapp/{bin,config,logs,data,scripts}
```

Create sample files:

Bash

```
touch ~/linux-training/day4/myapp/config/app.conf



touch ~/linux-training/day4/myapp/logs/app.log



touch ~/linux-training/day4/myapp/scripts/start.sh
```

Add content:

Bash

```
echo "APP_NAME=training-app" > ~/linux-training/day4/myapp/config/app.conf



echo "Application started" > ~/linux-training/day4/myapp/logs/app.log
```

Inspect:

Bash

```
ls -R ~/linux-training/day4/myapp
```

# Part 3 — Reading and inspecting files

00:45–01:05 · 20 minutes

Linux engineers frequently inspect configuration files, application logs, deployment scripts and system information.

Today's commands provide the foundation for that work.

## 3.1 `cat` — display file contents

Syntax:

Bash

```
cat FILENAME
```

Example:

Bash

```
cat ~/linux-training/day4/myapp/config/app.conf
```

Output:

Plain text

`APP_NAME=training-app`

Display multiple files:

Bash

```
cat file1.txt file2.txt
```

Create a file using a heredoc:

Bash

```
cat > sample.conf <<EOF

APP_NAME=demo

APP_PORT=8080

ENVIRONMENT=development

EOF
```

Inspect:

Bash

```
cat sample.conf
```

Explain:

* `cat` reads and displays file contents.
* It can display multiple files consecutively.
* It can also be used with shell redirection to create or write files.

Production caution: `cat` is convenient for small files. Avoid printing sensitive configuration files containing passwords, tokens or private keys into terminal recordings, shared screens or logs.

## 3.2 `less` — inspect large files

Imagine an application log containing 50,000 lines.

Using `cat` could flood the terminal.

Use:

Bash

```
less app.log
```

Useful keys:

| Key | Action |
| --- | --- |
| `Space` | Next page |
| `b` | Previous page |
| `/error` | Search for error |
| `n` | Next search match |
| `N` | Previous search match |
| `g` | Beginning of file |
| `G` | End of file |
| `q` | Quit |

Demonstration:

Bash

```
less /var/log/syslog
```

On Ubuntu systems where this file exists.

Alternative log location or service logging may apply on other distributions.

## 3.3 `head` — display the beginning of a file

Syntax:

Bash

```
head FILENAME
```

By default, it displays the first 10 lines.

Example:

Bash

```
head /etc/passwd
```

Display the first five lines:

Bash

```
head -n 5 /etc/passwd
```

## 3.4 `tail` — display the end of a file

Syntax:

Bash

```
tail FILENAME
```

Display the last five lines:

Bash

```
tail -n 5 /var/log/syslog
```

Follow a log file:

Bash

```
tail -f app.log
```

Explain:

`tail -f` keeps the command running and displays new content as it is appended.

Press `Ctrl+C` to stop following.

Production example:

A developer reports that an application deployment has failed.

The DevOps engineer opens the application log:

Bash

```
tail -f /var/log/myapp/app.log
```

Then asks the application team to reproduce the failure while observing new log entries.

## 3.5 `wc` — count lines, words and bytes

Examples:

Bash

```
wc app.log

wc -l app.log

wc -w app.log

wc -c app.log
```

Meaning:

| Option | Counts |
| --- | --- |
| `-l` | Lines |
| `-w` | Words |
| `-c` | Bytes |

Production example:

How many lines are in an application log?

Bash

```
wc -l app.log
```

Representative output:

Plain text

`250 app.log`

## 3.6 `grep` — search for text

Syntax:

Bash

```
grep PATTERN FILE
```

Example:

Bash

```
grep "ERROR" app.log
```

Useful options:

| Option | Meaning |
| --- | --- |
| `-i` | Case-insensitive search |
| `-n` | Show line numbers |
| `-v` | Show lines that do not match |
| `-r` | Search recursively |
| `-c` | Count matching lines |
| `-E` | Extended regular expressions |

Demonstrations:

Bash

```
grep -i "error" app.log
```

Bash

```
grep -n "ERROR" app.log
```

Bash

```
grep -c "ERROR" app.log
```

Bash

```
grep -v "INFO" app.log
```

Production example:

Bash

```
grep -i "failed" /var/log/syslog
```

Explain that this searches for lines containing `failed`, regardless of letter case.

Trainer note: Detailed pattern matching and regular expressions can be taught in a later text-processing lesson. Today, focus on basic searching.

# Part 4 — Copying, moving and renaming files

01:05–01:25 · 20 minutes

## 4.1 `cp` — copy files

Syntax:

Bash

```
cp SOURCE DESTINATION
```

Create a sample file:

Bash

```
cd ~/linux-training/day4/myapp



echo "APP_PORT=8080" > config/app.conf
```

Copy it:

Bash

```
cp config/app.conf config/app-backup.conf
```

Verify:

Bash

```
ls -l config
```

Explain that `cp` creates a separate copy of the file.

Inspect both:

Bash

```
cat config/app.conf

cat config/app-backup.conf
```

### Useful `cp` options

| Option | Purpose |
| --- | --- |
| `-i` | Ask before overwriting |
| `-r` | Copy directories recursively |
| `-v` | Show copied files |
| `-p` | Preserve mode, ownership where permitted, and timestamps |

Examples:

Copy a directory:

Bash

```
cp -r config config-backup
```

Ask before overwriting:

Bash

```
cp -i config/app.conf config/app-backup.conf
```

Show the copy operation:

Bash

```
cp -v config/app.conf config/app-copy.conf
```

Preserve file metadata where permitted:

Bash

```
cp -p config/app.conf config/app-preserved.conf
```

Explain:

* A normal copy creates another file with its own inode on the same filesystem.
* The contents are copied.
* The original file remains unchanged.
* Copying ownership may require elevated privileges.

## 4.2 `mv` — move files

Syntax:

Bash

```
mv SOURCE DESTINATION
```

Move a file:

Bash

```
mv config/app-copy.conf logs/
```

Verify:

Bash

```
ls -l logs/
```

Explain:

The file is moved from the source location to the destination.

When source and destination are on the same filesystem, a move commonly changes directory entries without copying all file data.

When they are on different filesystems, the operation may require copying the data and removing the original.

## 4.3 `mv` — rename files

In Linux, there is no separate standard `rename` command needed for ordinary file renaming. `mv` is commonly used.

Example:

Bash

```
mv logs/app-copy.conf logs/app-archive.conf
```

Verify:

Bash

```
ls -l logs/
```

Explain:

Renaming is a change in the file's name or directory entry, not necessarily a copy of its contents.

### Production scenario — configuration backup before change

A team wants to update an application configuration file.

A basic backup step could be:

Bash

```
cp -p /opt/myapp/config/app.conf \

      /opt/myapp/config/app.conf.backup
```

Then an authorised deployment process can update the configuration.

Why do we take a backup?

* It provides a previous version for comparison.
* It can support recovery if the change fails.
* It gives the team a reference for troubleshooting.

A backup on the same disk is not protection against disk failure. Production backup policies should include appropriate external or centralised backup storage.

# Part 5 — Removing files and directories safely

01:25–01:40 · 15 minutes

This topic deserves special attention because an incorrect removal command can cause data loss.

## 5.1 `rm` — remove files

Syntax:

Bash

```
rm FILENAME
```

Create a disposable test file:

Bash

```
cd ~/linux-training/day4



touch test-delete.txt

ls -l test-delete.txt
```

Remove it:

Bash

```
rm test-delete.txt
```

Verify:

Bash

```
ls -l test-delete.txt
```

The file should no longer be present.

### Useful options

| Option | Meaning |
| --- | --- |
| `-i` | Ask before each removal |
| `-f` | Force removal without prompting |
| `-r` | Remove directories and their contents recursively |
| `-v` | Display what is removed |

Demonstrate safer interactive removal:

Bash

```
touch sample.txt



rm -i sample.txt
```

The command asks for confirmation.

## 5.2 `rmdir` — remove empty directories

Create an empty directory:

Bash

```
mkdir empty-directory
```

Remove it:

Bash

```
rmdir empty-directory
```

Explain:

`rmdir` removes empty directories only.

If a directory contains files, it will fail.

## 5.3 Why is `rm -rf` dangerous?

You will frequently see this command in scripts and tutorials:

Bash

```
rm -rf DIRECTORY
```

Break it down:

* `rm` — remove.
* `-r` — recursively remove directories and their contents.
* `-f` — force removal without prompting.

This can delete a large directory tree without asking for confirmation.

High-risk command

Never run unfamiliar recursive deletion commands on production servers.

Especially avoid executing a command containing an unchecked variable:

Bash

```
rm -rf "$TARGET_DIR"/*
```

If `TARGET_DIR` is empty, incorrect or unexpectedly set, the command may target the wrong location.

Before a deletion operation, inspect the target:

Bash

```
printf 'Target: <%s>\n' "$TARGET_DIR"

ls -ld -- "$TARGET_DIR"
```

Also validate the variable and the intended target before running any removal command.

### 5.4 Production safety practices

1. Verify the exact file or directory path.
2. Check the current working directory using `pwd`.
3. Use `ls -ld` to inspect the target.
4. Prefer `rm -i` when practising or manually deleting uncertain files.
5. Follow change-management and backup requirements.
6. Never use `sudo` simply because a command failed due to permissions.

# Part 6 — Practical DevOps scenarios

01:40–01:55 · 15 minutes

Now connect the commands to tasks that students may encounter in Jenkins, GitHub Actions, Ansible, Docker, Kubernetes and cloud environments.

## Scenario 1 — Prepare an application deployment directory

Requirement: A deployment engineer needs to prepare an application directory on an Ubuntu VM.

Execute:

Bash

```
mkdir -p ~/deployments/myapp/{config,logs,backup,scripts}
```

Create files:

Bash

```
touch ~/deployments/myapp/config/app.conf

touch ~/deployments/myapp/logs/app.log

touch ~/deployments/myapp/scripts/deploy.sh
```

Add configuration:

Bash

```
cat > ~/deployments/myapp/config/app.conf <<EOF

APP_NAME=myapp

APP_PORT=8080

ENVIRONMENT=development

EOF
```

Verify:

Bash

```
ls -R ~/deployments/myapp

cat ~/deployments/myapp/config/app.conf
```

Ask students:

* Which command created the directories?
* Which command created the files?
* How was configuration written?
* How would you inspect the log file?

## Scenario 2 — Jenkins deployment fails because a file is missing

Problem:

A Jenkins pipeline reports:

Plain text

`cp: cannot stat 'target/application.jar': No such file or directory`

Explain:

`cp` is unable to find the source file specified in the command.

Possible investigation:

Bash

```
pwd

ls -la

ls -la target/

find . -type f -name "*.jar"
```

Ask students to identify possible causes:

* The build did not produce the JAR.
* The pipeline is running in the wrong workspace.
* The expected filename is incorrect.
* The build output directory is different.
* An earlier pipeline stage failed.

DevOps lesson: Before changing a deployment command, confirm that the build actually generated the expected artifact.

## Scenario 3 — A configuration change needs a backup

Problem:

The team needs to modify an application configuration file.

Demonstrate:

Bash

```
cp -p ~/deployments/myapp/config/app.conf \

      ~/deployments/myapp/backup/app.conf.backup
```

Verify:

Bash

```
ls -l ~/deployments/myapp/backup

stat ~/deployments/myapp/config/app.conf

stat ~/deployments/myapp/backup/app.conf.backup
```

Ask students:

Why is `cp -p` useful here?

Expected answer: It preserves relevant file metadata where permitted, in addition to copying the file content.

## Scenario 4 — Application log investigation

Problem:

An application is reporting intermittent errors.

Create test log entries:

Bash

```
cat > ~/deployments/myapp/logs/app.log <<EOF

2026-11-03 10:00:00 INFO Application started

2026-11-03 10:01:00 INFO Database connected

2026-11-03 10:02:00 ERROR Database connection timeout

2026-11-03 10:03:00 INFO Retry initiated

2026-11-03 10:04:00 ERROR Database connection failed

EOF
```

Find errors:

Bash

```
grep -i "error" ~/deployments/myapp/logs/app.log
```

Show line numbers:

Bash

```
grep -in "error" ~/deployments/myapp/logs/app.log
```

Count errors:

Bash

```
grep -ic "error" ~/deployments/myapp/logs/app.log
```

Show the last entries:

Bash

```
tail -n 3 ~/deployments/myapp/logs/app.log
```

Explain that these commands help narrow down an investigation, but the engineer must correlate the errors with application behaviour, service status and other system evidence.

## Scenario 5 — Ansible and Linux file management

Explain that configuration-management tools automate the same kinds of operations.

For example, Ansible has modules for:

| Linux operation | Ansible module |
| --- | --- |
| Create directory | `ansible.builtin.file` |
| Copy file | `ansible.builtin.copy` |
| Create symbolic link | `ansible.builtin.file` |
| Remove file | `ansible.builtin.file` |
| Render configuration template | `ansible.builtin.template` |

A basic Ansible task to create a directory:

YAML

```
- name: Create application directory

  ansible.builtin.file:

    path: /opt/myapp/logs

    state: directory

    mode: "0755"
```

Explain:

The Linux commands are the foundation. Ansible automates these operations consistently across multiple servers.

# Part 7 — Student practical assessment

Ask students to complete this exercise independently, without copying commands from the previous examples.

15-minute lab challenge

Scenario: You have joined a DevOps team. Your lead asks you to prepare a small application deployment workspace, create configuration and log files, back up the configuration and investigate errors.

### Task 1 — Create the directory structure

Plain text

`day4-assessment/
├── application/
│ ├── config/
│ ├── logs/
│ ├── scripts/
│ └── data/
└── backup/`

### Task 2 — Create files

Create:

* `application/config/app.conf`
* `application/logs/app.log`
* `application/scripts/start.sh`

### Task 3 — Add configuration

Add the following values to `app.conf`:

Plain text

`APP_NAME=student-app
APP_PORT=8080
ENVIRONMENT=testing`

### Task 4 — Add log entries

Add these entries to `app.log`:

Plain text

`INFO Application started
INFO Database connected
ERROR Database timeout
INFO Retry initiated
ERROR Database connection failed`

### Task 5 — Investigate

Find all errors and display their line numbers.

Count the number of error entries.

### Task 6 — Create a backup

Copy `app.conf` into the `backup` directory while preserving relevant metadata.

### Task 7 — Verify

Show:

* The complete directory structure.
* The configuration file content.
* The log file content.
* The backup file metadata.

Trainer evaluation: Award marks for correct commands, explanation of each command, verification and safe handling—not just successful execution.

# Part 8 — Day 4 knowledge check

Test your understanding

0/7 answered

1. Which command creates a directory including missing parent directories?

touch -p

mkdir -p

cp -p

2. Which command copies a file?

mv

cp

touch

3. Which command displays the last 10 lines by default?

head

cat

tail

4. Which operator appends output to a file?

>

>>

<

5. What does rm -r do?

Renames files

Recursively removes directories and their contents

Creates directories

6. Which command identifies a file's type?

file

stat

pwd

7. What does grep -n provide?

File permissions

Line numbers for matching lines

File size

Submit answers

# Day 4 homework

1. Explain the difference between `cp` and `mv`.
2. Explain the difference between `>` and `>>`.
3. What is the difference between `head` and `tail`?
4. What does `stat` tell us that a normal `ls` listing may not show?
5. Explain why `rm -rf` is dangerous.
6. Create a directory structure for a sample Python application.
7. Create a configuration file, append three values and inspect it.
8. Create a backup of that configuration.
9. Add five log entries and use `grep` to find errors.
10. Explain how Ansible automates Linux file-management operations.

Bonus production question: A Jenkins pipeline successfully builds an application but fails at the copy stage because the artifact cannot be found. Explain how you would investigate the problem without immediately modifying the pipeline.

## Training progress

## Linux fundamentals — progress

Day 1

Operating systems and Linux architecture

Covered

Day 2

Linux boot process and system initialisation

Covered

Day 3

Filesystem hierarchy and navigation

Covered

Day 4

Essential Linux file-management commands

Covered

Next: Day 5 — Linux text processing and file searching

We will cover `find`, `grep` in more depth, `cut`, `sort`, `uniq`, `tr`, `wc`, `sed` and `awk`, using real application logs and DevOps troubleshooting examples.

# Linux Shells

For many of us, one of the first commands we ever typed into a dark terminal was:

```bash
ping
```

That black window is commonly associated with the **shell** — a command-line interface that allows users to interact with an operating system.

A shell acts as an interpreter between the user and the operating system. It reads commands, parses them, and executes the appropriate programs or built-in operations. The executed programs can then interact with the Linux kernel through system calls.

Linux supports a wide variety of shells. While many of them share common features, each shell has its own design philosophy, syntax, performance characteristics, and scripting capabilities.

This document introduces eight historically important and commonly encountered shells:

1. Bourne Shell (`sh`)
2. C Shell (`csh`)
3. TENEX C Shell (`tcsh`)
4. KornShell (`ksh`)
5. Debian Almquist Shell (`dash`)
6. Bourne Again Shell (`bash`)
7. Z Shell (`zsh`)
8. Friendly Interactive Shell (`fish`)

---

# What Is a Shell?

A shell is a program that provides a command-line interface (CLI) to the operating system.

A simplified execution flow looks like this:

```text
User
  │
  ▼
Terminal
  │
  ▼
Shell
  │
  ├── Parse command
  ├── Expand arguments
  ├── Locate executable
  └── Execute program
          │
          ▼
      System Calls
          │
          ▼
      Linux Kernel
```

For example, when you run:

```bash
cat file.txt
```

the shell parses the command, locates the `cat` executable, and starts it with `file.txt` as an argument. The `cat` process then interacts with the kernel to access the file and display its contents.

---

# 1. Bourne Shell (`sh`)

The **Bourne Shell**, commonly referred to as `sh`, was developed by Stephen Bourne at Bell Labs and became one of the foundational Unix shells.

It introduced many concepts that later became fundamental to Unix shell scripting.

Historically, early versions were relatively minimal compared with modern interactive shells. Features such as sophisticated command history, interactive completion, and convenient arithmetic operations were either unavailable or limited.

### Typical characteristics

* Lightweight and fast
* Strong foundation for shell scripting
* Simple syntax
* Widely used as a compatibility shell
* Served as the foundation for many later shells

The shell executable was traditionally located at:

```text
/bin/sh
```

On modern Unix-like systems, `/bin/sh` may be a symbolic link to another shell such as `dash` or `bash`.

![Bourne Shell](https://mihanwebhost.com/blog//inlinePhotos/1689064533image2.webp)

---

# 2. C Shell (`csh`)

The **C Shell**, or `csh`, was developed by Bill Joy at the University of California, Berkeley.

Its syntax was influenced by the **C programming language**, making some aspects of the shell more familiar to C programmers.

Unlike the traditional Bourne shell, `csh` focused more heavily on interactive use and introduced several convenient features.

### Notable features

* Command history
* C-like syntax
* Aliases
* Job control
* Convenient interactive features
* The `~` notation for the user's home directory

Typical prompt conventions included:

```text
%
#
```

where `%` was commonly associated with normal users and `#` with the root account.

The executable was traditionally located at:

```text
/bin/csh
```

Despite its historical importance, `csh` has several scripting limitations and is generally not recommended for writing complex shell scripts today.

![C Shell](https://mihanwebhost.com/blog//inlinePhotos/1689064567image9.webp)

---

# 3. TENEX C Shell (`tcsh`)

**TENEX C Shell**, better known as `tcsh`, is an enhanced version of `csh`.

It incorporated features inspired by the TENEX operating system while retaining compatibility with C Shell syntax.

`tcsh` became particularly popular on BSD systems and was also used in earlier Unix environments.

### Notable features

* Advanced command history
* Command-line editing
* Filename completion
* Job control
* Improved interactive experience
* Enhanced command searching

A typical `tcsh` environment could display information such as the hostname and current directory in the prompt.

The executable is commonly found at:

```text
/bin/tcsh
```

or:

```text
/usr/bin/tcsh
```

![TENEX C Shell](https://mihanwebhost.com/blog//inlinePhotos/1689064585image1.webp)

---

# 4. KornShell (`ksh`)

**KornShell**, or `ksh`, was developed by David G. Korn at Bell Labs.

It was designed to combine the strengths of the Bourne shell with powerful interactive features inspired by other Unix shells.

KornShell introduced improvements in areas such as:

* Arithmetic operations
* Command-line editing
* Job control
* Functions
* Command history
* Shell scripting
* Performance

Common executable locations include:

```text
/bin/ksh
```

and, depending on the implementation:

```text
/bin/ksh93
```

KornShell became particularly influential in Unix environments and contributed many ideas that later appeared in other shells.

---

# 5. Debian Almquist Shell (`dash`)

The **Debian Almquist Shell**, commonly known as `dash`, is a lightweight POSIX-compatible shell derived from the Almquist shell family.

It is widely used on Debian-based systems, including Ubuntu, particularly for system scripts.

Its primary goals include:

* Small size
* Fast startup
* Low memory usage
* POSIX compatibility

On many Debian-based systems, `/bin/sh` points to `dash`.

You can check this with:

```bash
ls -l /bin/sh
```

![Debian Almquist Shell](https://mihanwebhost.com/blog//inlinePhotos/1689064658image7.webp)

### `dash` vs `bash`

One important distinction is that `dash` is designed around **POSIX shell compatibility**, while `bash` provides many additional features that are not part of the POSIX standard.

Therefore, a script written specifically for Bash may not work correctly when executed with:

```bash
sh script.sh
```

A Bash script should generally specify its interpreter explicitly:

```bash
#!/usr/bin/env bash
```

---

# 6. Bourne Again Shell (`bash`)

**Bash**, short for **Bourne Again Shell**, is one of the most widely used shells in the Linux ecosystem.

It was developed as a free and compatible replacement for the original Bourne Shell.

Bash combines traditional Bourne-shell scripting with extensive interactive and scripting features.

### Major features

* Conditional statements such as `if`
* Loops
* Functions
* Command history
* Tab completion
* Brace expansion
* Parameter expansion
* Job control
* Signal handling
* Shell scripting
* Extensive command-line customization

For example:

```bash
for file in *.txt; do
    echo "$file"
done
```

Bash also maintains a high degree of compatibility with traditional Bourne-shell scripts, although not every `sh` script should automatically be assumed to be Bash-specific.

![Bash](https://mihanwebhost.com/blog//inlinePhotos/1689064694image4.webp)

You can check your current shell with:

```bash
echo "$SHELL"
```

and identify Bash specifically with:

```bash
bash --version
```

---

# 7. Z Shell (`zsh`)

**Z Shell**, or `zsh`, is a powerful interactive shell with extensive customization and scripting capabilities.

It incorporates ideas and features found in several Unix shells while providing a highly customizable user experience.

### Notable features

* Advanced tab completion
* Command-line editing
* Powerful globbing
* Spelling correction
* Advanced history management
* Extensive customization
* Plugin support
* Multiple compatibility modes
* Programmable prompts

The executable is commonly located at:

```text
/bin/zsh
```

or:

```text
/usr/bin/zsh
```

`zsh` is particularly popular among developers and power users who want a highly customizable terminal environment.

![Z Shell](https://mihanwebhost.com/blog//inlinePhotos/1689064738image5.webp)

---

# 8. Friendly Interactive Shell (`fish`)

The **Friendly Interactive Shell**, commonly known as `fish`, was designed from the ground up to provide a modern and user-friendly command-line experience.

Unlike traditional shells, `fish` does not attempt to maintain strict POSIX shell compatibility.

### Notable features

* Syntax highlighting
* Intelligent autosuggestions
* Advanced tab completion
* Command history search
* Web-based configuration
* User-friendly defaults
* Powerful interactive features

The executable is commonly located at:

```text
/usr/bin/fish
```

One of the most noticeable features of `fish` is its intelligent command suggestion system.

For example, as you type:

```bash
git che
```

`fish` may suggest:

```bash
git checkout
```

![Friendly Interactive Shell](https://mihanwebhost.com/blog//inlinePhotos/1689064815image3.webp)

### The main trade-off

The biggest consideration when switching to `fish` is its lack of POSIX compatibility.

A script written for:

```bash
sh
```

or:

```bash
bash
```

should not automatically be expected to work as a `fish` script.

---

# Shell Comparison

| Shell  | Main Focus                |  POSIX | Interactive Features | Common Use                   |
| ------ | ------------------------- | -----: | -------------------: | ---------------------------- |
| `sh`   | Portability & scripting   |    Yes |                  Low | System scripts               |
| `csh`  | Interactive Unix shell    |     No |               Medium | Historical / legacy          |
| `tcsh` | Enhanced `csh`            |     No |                 High | BSD / legacy systems         |
| `ksh`  | Scripting & performance   | Mostly |                 High | Unix environments            |
| `dash` | Lightweight POSIX shell   |    Yes |                  Low | Debian/Ubuntu system scripts |
| `bash` | General-purpose shell     | Mostly |                 High | Linux / scripting            |
| `zsh`  | Interactive customization | Mostly |            Very High | Developers / power users     |
| `fish` | User-friendly interaction |     No |            Very High | Modern interactive use       |

---

# Final Thoughts

Although these shells share the same fundamental purpose, they were designed with different priorities.

At a high level:

```text
sh
 │
 ├── Portability
 │
 ├── csh ──► tcsh
 │
 ├── ksh
 │
 └── bash
       │
       └── zsh

dash ──► Lightweight POSIX scripting

fish ──► Modern interactive experience
```

For modern Linux users, the most relevant choices are generally:

* **Bash** — excellent general-purpose shell and scripting environment
* **Zsh** — powerful and highly customizable interactive shell
* **Fish** — excellent interactive experience with user-friendly defaults
* **Dash** — lightweight and efficient for system-level POSIX scripts

Understanding multiple shells is valuable because Linux systems, servers, containers, scripts, and development environments may use different shells.

The key is not simply knowing how to type commands, but understanding **how the shell interprets those commands and how they ultimately interact with the operating system.**

---

## Quick Reference

Check the current shell:

```bash
echo "$SHELL"
```

Check the shell used by the current process:

```bash
ps -p $$ -o comm=
```

Find installed shells:

```bash
cat /etc/shells
```

Start another shell:

```bash
bash
```

```bash
zsh
```

```bash
fish
```

Exit the current shell:

```bash
exit
```

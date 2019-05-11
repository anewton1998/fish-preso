---
title: 15 Minutes with the Fish Shell
author: Andy Newton @rcode3@masto.rootdc.xyz
patat:
  wrap: true
  margins:
    left: 5
    right: 5
  theme:
    header: [vividRed,bold]
    emph: [vividCyan]
    code: [vividGreen,bold]
    codeBlock: [vividGreen,bold]
...


        +----------------------------------------------+
        |                                              |
        |        15 Minutes with the Fish Shell        |
        |        ------------------------------        |
        |                                              |
        |                  Andy Newton                 |
        |               Escape Key Refugee             |
        |                 Not an expert!               |
        |        https://masto.rootdc.xyz/@rcode3      |
        |                                              |
        +----------------------------------------------+


---

# Fish - the Friendly Shell

  >
  > Finally, a command line shell for the 90's!
  >

. . .

Or things we should have had some time ago:

- Out-of-the-box Awesome!
- VGA colors!
- Autosuggestions
- A not-so-messed-up scripting language

. . .

## But... but...

It is true that you can do some of these parlor tricks with Bash, ZSH, etc... using add-ons,
but Fish offers this out of the box.

Plus, Fish has its own add-ons community.

---

# About This Presentation

> - Simple Demonstration
> - Versions
> - Installation
> - Configuration and Config files
> - Fish "package managers"
> - Virtual language / execution environments
> - Tricks and Tips

# The Authoritiative Source

https://fishshell.com/

---

# Simple Demonstration

- Fish for the first time.
- Fish using bobthefish
- Autosuggestion for files with tab
- Autosuggestion for files with double-tab
- Autosuggestion for history
- Page up for history
- Syntax highlighting

---

# Versions

Fish v3 was released in December, 2018 (current as of now is 3.0.2).

Some distributions have 2.x.x (usually, 2.7.1).

There are some breaking changes between 2.7.1 and 3.0.0. However, most of these changes seem to be
esoteric. Your mileage may vary, but if you are new to Fish then it is likely you will not be
impacted by them.

See the release notes at https://fishshell.com/release_notes.html

---

# How to Install

## User Your Distributions Package Manager

The prefered and easiest way to install Fish is with your system's package manager.

    # deb / ubuntu
    apt install fish
    
    # arch, etc...
    pacman -S fish
    
    # fedora
    dnf install fish 

For distributions that do not have Fish in their repositories, you will need to add
the Fish repo to your systems package manager. See https://fishshell.com/ -> Go Fish.

Some distributions will have version 2.7.1. Version 3.0.2 is the latest.
If your distribution has the old version and you want the new one, add the Fish repos
to your system package manager and then install. See https://fishshell.com/ -> Go Fish.

---

# How to Install

## The Hard Way (because you hate yourself)

Install these dependencies:

- a C++11 compiler (g++ 4.8 or later, or clang 3.3 or later)
- CMake (version 3.2 or later)
- a curses implementation such as ncurses (headers and libraries)
- PCRE2 (headers and libraries) - a copy is included with fish
- gettext (headers and libraries) - optional, for translation support

Download the source tar from GitHub: https://github.com/fish-shell/fish-shell

Then

    mkdir build; cd build
    cmake ..
    make
    sudo make install

---

# How to Install

## To Simply Play With It

Just type `fish`

## To Set As Your Default Shell

`chsh -s /usr/local/bin/fish`

where `/usr/local/bin/fish` is where fish binary is located.


---

# Configuration

## The Fast Way

Typing `fish_config` will open your browser to a fish configuration app. 

This is an easy to experiment and
customize Fish so it looks dope or chill or savage or whatevs in no time.


---

# Config Files

## The .bashrc

When Fish starts, it executes `~/.config/fish/config.fish` 

This is the equivalent to `/.bashrc`

## Autoloading Functions

When fish encounters a command, it attempts to autoload a function for that command, 
by looking for a file with the name of that command in `~/.config/fish/functions/`

For example, if you wanted to have a function `ll`, you would add a text file 
`ll.fish` to `~/.config/fish/functions`

    function ll
        ls -lh $argv
    end

---

# Fish "Package Managers"

For many shells, there exist third party add-ons such as extensions, themes, etc...

To help install third-part add-ons, there exist third-party "package managers" for the shells.

Fish is no exception.

---

## Oh My Fish!

Quite popular!

To install:

    curl -L https://get.oh-my.fish | fish

See https://github.com/oh-my-fish/oh-my-fish

---

## Fisher

The author seems to write a lot of extensions/add-on packages for Fish as well.

To install:

    curl https://git.io/fisher --create-dirs -sLo ~/.config/fish/functions/fisher.fish

See https://github.com/jorgebucaran/fisher

Package compatible with Oh My Fish!

---

## Fundle

A minimalist package manager for fish inspired by Vundle.

To install:

    curl -sfL https://git.io/fundle-install | fish

See https://github.com/danhper/fundle 

Also package compatible with Oh My Fish!

---

# Virtual Language / Execution Environments

A lot of developers use virtual language/execution environments, or just Virtual Environment (VE),
 to manage and use multiple versions of a programming language and it's runtime.

These are not VMs or containers, just scripts that manipulate the shell environment.

Language   VE
---------- ----------
Node       nvm
Ruby       rvm, rbenv
Python     virtualenv
Java/JVM   sdkman

Most of them expect to manipulate Bash, and therefore don't work natively with Fish.

So the Fish community has created VEs for these languages.

---

# Fish Virtual Environments

Language   VE         Fish VE
---------- ---------- -----------
Node       nvm        fish-nvm
Node       nvm        plugin-nvm
Ruby       rvm        plugin-rvm 
Ruby       rbenv      plugin-rbenv
Python     virtualenv virtualfish
Python     virtualenv pyenv
Java/JVM   sdkman     skdman-for-fish
Java/JVM   sdkman     omf-sdk

And there are generic wrappers for the VEs

-------- ----------------------------------------
bass     https://github.com/edc/bass
fish-bax https://github.com/jorgebucaran/fish-bax
-------- ----------------------------------------

---

# Tip: Set the Path, Now and Forever

If you need to add a directory to your path:

    set -U fish_user_paths /usr/local/bin $fish_user_paths

This adds `/usr/local/bin` to the current path of your current shell and all
other fish shells that are active, now and in the future.

---

# Tip: Install the Powerline Font

A lot of the symbols and fancy prompts used by many of the themes from
Oh My Fish use the Powerline Font.

See https://github.com/powerline/fonts

For most distributions, you can simply use your system package manager to install them.

---

# Tip: Use the functions Command

Many of the Fish commands are simple Fish functions. If you want to see how they work
just type `functions` followed by the command name:

    functions ll

---

# Further Reading

- Programming the Fish Shell

    * Nicolas Vanhoren : https://nicolas-van.github.io/programming-with-fish-shell

- Fish Cookbook

    * Jorge Bucaran : https://github.com/jorgebucaran/fish-cookbook

- Fish Awesome

    * Jorge Bucaran : https://github.com/jorgebucaran/awesome-fish

And https://fishshell.com

---

# Questions?

## About This Presentation

------------ -----------------------------------------
Author       Andy Newton
             https://masto.rootdc.xyz/@rcode3
             @rcode3@masto.rootdc.xyz

Presentation https://github.com/anewton1998/fish-preso
Repository

Presentation Patat
Tool         Terminal-based presentation using Pandoc
             https://github.com/jaspervdj/patat
------------ -----------------------------------------

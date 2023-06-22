---
layout: post
title: Fish Shell Setup
date: '2023-01-28'
author: Christopher Slade
description: I switched to fish shell and I wanted to document how I set it up.
tags: 
  - technology
  - terminal
---

The auto completions on my zsh setup were bugging me a little bit. It seemed to go through my history and suggest commands that didn't work. I didn't remember this when I used fish from before.  Since switching between shells is easy, I decided to try fish and see if I could get it to run.  Everything worked and less than 20 minutes later I was using fish.

Here is what I did:

1. Install fish with homebrew. 
1. On a new install you would want to install and set up starship prompt, but since I already did that with zsh, I didn't have to do anything. Just use the same setup and config file from the previous post.
1. To enable starship prompt on fish add `fish_add_path "/opt/homebrew/bin/"` to the `~/.config/fish/config.fish` file. And add `starship init fish | source` to enable starship.
1. I also set the default editor in the config file: `set -gx EDITOR vim`.
1. Install exa for a better ls: `brew install exa`, and set the alias in the config file: `alias ls='exa -lag --header'`.
1. Install [fisher](https://github.com/jorgebucaran/fisher) to install plugins.
1. Install plugin for rbenv [fish-rben](https://github.com/rbenv/fish-rbenv).
1. Install plugin for sdkman [fish-sdkman](https://github.com/reitzig/sdkman-for-fish).

If I ever need to switch back to zsh, I just need to change the default shell.

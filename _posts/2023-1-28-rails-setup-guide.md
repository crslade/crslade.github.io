---
layout: post
title: Terminal and Rails Setup Guide
date: '2023-01-28'
author: Christopher Slade
description: I wanted to document how I install and set up things on my development machine because I often forget how I set everything up and I don't want to start from square one every time. I decided to record it here so I can find it when I need it.
tags: 
  - technology
  - rails
  - terminal
---

I wanted to document how I install and set up things on my development machine because I often forget how I set everything up and I don't want to start from square one every time. I decided to record it here so I can find it when I need it.

Previously, I was using [oh-my-zsh](https://ohmyz.sh) as my shell prompt. I liked all of the plugins and that I could theme it how I wanted. Then, I started using spaceship as the prompt. Then, as I upgraded, I found that spaceship was upgraded to [starship](https://starship.rs). That lead me to find the [fish shell](https://fishshell.com).

I liked the fish shell, but it was hard to integrate all of my other software to work with it, especially [puma-dev](https://github.com/puma/puma-dev) which allows me to use a test domain for all of my different apps. So, I wanted to stick with zsh and starship.

To set it up, you need to install the following items.

1. Install [oh-my-zsh](https://ohmyz.sh) following the instructions on the website.
1. Install starship with homebrew.
1. Install [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions) and [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting) with homebrew. Make sure to copy down the instructions brew prints out at the end of the installation (for both packages). You will need to copy them into your .zshrc file.

After you have installed it all you need to edit your .zshrc file.

First, comment out the default theme `ZSH_THEME="robbyrussell"` because we will use starship for that.

Then add the Starship prompt initialization to the bottom of your .zshrc file. 

    #Starship Prompt
    eval "$(starship init zsh)" 

Then you can customize your prompt by adding a configuration file at `~./config/starship.toml`. I found a good [guide on YouTube](https://www.youtube.com/watch?v=VgTu1_92U0U). It is super easy to customize. Here is my final configuration.

<script src="https://gist.github.com/crslade/2e23f91f8d531aee5b5b6b5b4e38a458.js"></script>

You can add the initialization of the zsh-autosuggetions and zsh-syntaz-highlighting below the starship prompt. zsh-syntax-highlighting should go at the very end of the .zshrc file. I recommend following the instructions that homebrew gives after you install the packages. But, here is what I needed to add to my file:

    #Auto Suggestions
    source /opt/homebrew/share/zsh-autosuggestions/zsh-autosuggestions.zsh

    #Syntax highlighting
    source /opt/homebrew/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh


Then you can add oh-my-zsh plugins. You will find a line in your .zshrc file that says `plugins=(git)`. I added git, bundler, ruby, and rails.

Then to install ruby I use rbenv and ruby-build. Install both of those with homebrew. You need to put the rbenv initialization in your `.zshrc` file. I also use homebrew to install postgresql and puma-dev. Puma-dev needs you to run two commands (one with sudo and one without).

I did try [warp](https://www.warp.dev), but for some reason, I couldn't get starship to work with it, even though it says it does. It seems like warp shows a lot of promise but I am not sure I like the idea of having to have an account that could track my shell activity.


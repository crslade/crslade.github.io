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

To set it up, I installed starship with homebrew. Then I needed to put the following in the .zshrc file:

    #Starship Prompt
    eval "$(starship init zsh)" 

Then you can customize your prompt by adding a configuration file at `~./config/starship.toml`. I found a good [guide on YouTube](https://www.youtube.com/watch?v=VgTu1_92U0U). It is super easy to customize. Here is my final configuration.

Then for better autocompletion I used `zsh-autosuggestions`. I installed it using homebrew. Don't forget to source it in .zshrc according to the instructions homebrew gives after you install it.

<script src="https://gist.github.com/crslade/2e23f91f8d531aee5b5b6b5b4e38a458.js"></script>

Then to install ruby I use rbenv and ruby-build. Install both of those with homebrew. You need to put the rbenv initialization in your `.zshrc` file. I also use homebrew to install postgresql and puma-dev. Puma-dev needs you to run two commands (one with sudo and one without).

I did try [warp](https://www.warp.dev), but for some reason, I couldn't get starship to work with it, even though it says it does. It seems link warp shows a lot of promise but I am not sure I like the idea of having to have an account that could track my shell activity.


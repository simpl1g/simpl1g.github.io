---
layout: post
title:  "Tips for web developers under WSL 2"
date:   2021-11-18 14:56:55 +0100
tags: development wsl2
---

As a Ruby Developer I use Windows only if I want to play some games, because it is pretty hard to work with it. 
However WSL 2 is big step toward and I decided to try it. 
Previously I tried WSL 1 and it was painful to setup project, a lot of bugs and segfaults. 
With WSL 2 things are getting much better. 
In this post I'm not going to describe how to install it, it is pretty straightforward now, but more about useful stuff.

#### Install [Windows Terminal][win-term]
It is much better than default terminal, you can even use ctrl+c and ctrl+v 😆

#### Setup your user 
By default you will be logged in as `root` user, it is not very good to have access to everything by default. I suggest creating separate sudo user 

```shell
sudo adduser simpl1g
```

You will be asked some questions along with password and at the end, you’ll be prompted to confirm that the information you entered is correct.
Also add user to sudoers so that you can run commands as administrator
```bash
sudo usermod -aG sudo simpl1g
```

#### Set newly created user as default for WSL
Open default command prompt or PowerShell and run
```bash
ubuntu config --default-user simpl1g
```

#### Set default profile and folder for Windows Terminal

I found [this answer][so-answer] very usefull. So in the end I have in `settings.json`
```ruby
{ 
  "defaultProfile": "{2c4de342-38b7-51cf-b940-2309a097f518}" # Automatically open Terminal with Ubuntu
  ...
  {
    "colorScheme": "Solarized Dark",                         # Use Solarized color scheme of terminal
    "guid": "{2c4de342-38b7-51cf-b940-2309a097f518}",
    "hidden": false,
    "name": "Ubuntu",
    "source": "Windows.Terminal.Wsl",
    "startingDirectory": "\\\\wsl$\\Ubuntu\\home\\simpl1g"   # Default folder for your new user 
  }
}
```

Now you can start development like in normal Ubuntu, I was able to install and launch everything that was required for my daily work project. Happy coding)

[win-term]: https://aka.ms/terminal
[so-answer]: [https://stackoverflow.com/a/66381106/1805815]

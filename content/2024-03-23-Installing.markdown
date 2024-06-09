---
categories: ['meta']
date: "2024-03-23T00:00:00Z"
title: Installing Jekyll on a Mac in March 2024
---
**Why**

- I wanted to run Jekyll on my Mac to see changes locally.

**Process**

- Follow the quickstart guide on official Jekyll website

- Problem 1: `gem install jekyll` received no output.

- Solution: terminal helpfully warned that.

>You don't have /Users/username/.gem/ruby/2.6.0/bin in your PATH, gem executables will not run.

- Problem 2: find the PATH

- Solution: (a) ```echo @$PATH``, (b) edit ```.bash_profile```

- Problem 3: still no Jekyll

- Use the ```which``` command to find out why Jekyll isn't recognised
- Use [this 10 year old answer](https://stackoverflow.com/questions/8146249/jekyll-command-not-found) ```$ gem install -n /usr/local/bin jekyll```

- Problem 4: nuked .```bash_profile``` somewhere in the process, so that couldn't even  ```ls``` or ```cd``` anywhere
- Solution: used this [fix](https://apple.stackexchange.com/questions/22859/bash-ls-command-not-found), i.e. temporarily assign an echo path to revive ```ls``` and ```cd```, and then fix the ```.bash_profile file```, where my mindless additions overwrote pre-existing paths!

**Reflections**

- Budget in the time with tinkering, and enjoying the classic early computer experience.

- Environment variables is something I should learn about, as it surfaces time and again as I went about fixing issues.

**Unresolved**

Running ```~/.bash_profile``` in bash in VS Code Terminal and Terminal yields different results.
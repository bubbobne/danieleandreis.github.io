---
title: "Git: Time to Clean Up My Workflow"
date: 2026-04-26
draft: false
tags: ["git", "programming"]
categories: ["programming"]
---


I started using version control systems many years ago with Subversion (SVN). Later, I tried other systems such as Bazaar, and finally, like many projects and developers, I moved to Git.

Now I can say that I have been using Git for several years, mostly as a practical tool to manage my code and keep track of changes. In most cases, especially at work, I use it for projects where I am the only developer, or I access repositories created by other people mainly for testing, not as an active developer.

Recently, however, I have been involved in a project with other people, and I realized that my understanding of Git is often superficial. I know how to use the main commands, but I do not always fully understand what is happening behind them.

For this reason, I want to go back to Git with a different approach: not just using it, but trying to understand its logic more deeply.

After re-reading the manual, [Pro Git](https://git-scm.com/book/en/v2), I noticed something interesting. If I compare my old notes with my new notes, they reflect a different aim. My first notes were mainly about hooks and configuration, with only a superficial focus on conflict management.

In the past, I had already thought about the best way to manage branches after reading the famous post [A Successful Git Branching Model](https://nvie.com/posts/a-successful-git-branching-model/). At the time, I understood the general idea and adopted part of it, but I did not explore it deeply.

Now I want to go more in depth into branching strategies, starting from Martin Fowler’s article on [branching patterns](https://martinfowler.com/articles/branching-patterns.html).

For now, my first goals are:

- Maintain cleaner repositories  
- Use private or temporary branches in a better way  

For example, especially in my private projects, I sometimes:

- Repeat the same commit message instead of amending the previous commit  
- Create unnecessary commits instead of updating the last one  

From now on, I want to use the `--amend` command more consciously:

```bash
git commit --amend
```

For unpushed branches, I also want to:

- Use rebase instead of merge (when possible)
- Keep a cleaner and more linear history


This post is just a starting point. As I encounter important cases or discover concepts that deserve more attention, I will write new posts to clarify them and improve my workflow step by step.

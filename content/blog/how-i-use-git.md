---
path: how-i-use-git
date: 2020-08-23T18:27:14.103Z
title: How I use Git
description: How I learnt and improved the way I work with others using the most
  universal programmer's tool
---
Having graduated a coding bootcamp nearly two years ago, I began the journey of learning how to use the principles of software engineering I’d learnt in real life software. I found a huge disconnect between being able to create variables, loops and maps, and having the ability 

I first delved deep into improving my Javascript, no bad move, however, software engineering is principally about collaboration, about writing software that is maintainable and extendable and to that end, no skill has helped me more when collaborating with other engineers than being able to use Git.

I had learned a bit of Git on the bootcamp - how to commit, push, pull. But understanding the basics was holding me back - using git in the cli was intimidating and I wasn’t sure always what was going on so I was reticent to experiment for fear of losing changes.

Thanks to help from my colleagues and good old fashioned practice - I feel I have now graduated from git absolute noob to git fairly beginner status! The point here is that while I’m by no means an expert, I’ve managed to get a lot of extra value by investing just a bit more time in git, and think other beginners will too.

## Why is Git important?
## My Git tips
### Own your toolbox
If you read the Pragmatic Programmer (and you should), you will read a chapter that talks about the tools that you use in your trade. The key lesson I remember is that while you will have a few trusty programs that you’ll come back to time and again (kind of like your trusty hammer) - you don’t need one tool for all jobs, in fact in the case of git, you may not want to use one tool for one job.

I initially learnt to use git using the command line and the lack of visibility combined with the lack of knowledge of how to use commands such as `git diff` impacted my confidence using git. So I installed Sourcetree, a desktop app for everything git. Sourcetree is great. The array of menus doesn’t just give you a nicer view of your branches and commits - but let’s you see some of the git actions that you can use which is a great learning exercise.

On top of this, I also use the git tool included in VS code, which lets me easily see my current changes, staged and unstaged, and add hunks (more on that later) from inside my code editor. Something you can also do in the other two tools, but I like doing it in VS code.

I even still use the cli when I want to quickly push, pull, even commit. So yeah. I use three tools to manage may git workflow when developing and each serve a purpose. It’s something that I’ve moulded while practicing and am totally open to changing as I find better tools for me. It’s not a ‘right’ way, it’s the way I feel comfortable working and you have to try a few things to get there.

### Committing
There are a lot of good resources on good commit messages etc, but I prefer here to focus on the purpose of my commits and hope that’ll inform the rest.

I use two types of commit:

**Saves** - I’ve got something working, or want a snapshot in time I can revert to if required.

**Logs** - Commits that tell my PR reviewer the story of the how and more importantly, the why.

Key here is to note that I’m usually in a mode. I won’t be alternating between save and log commits, but will be developing a feature, often when I’m in the stage of discovering unknowns or working out how to implement something - then I will be doing seemingly more random save commits. 

When submitting a PR - I think it’s important to be able to tell your reviewer a story about how you implemented your change. Using a history of well organised commits is a great way to achieve this, so I will often re-write my commits when it comes to review time to try and turn the commits on my branch into something that flows nicely. This involves something called rebasing which can be intimidating and is what the next section is all about.

### Rebasing
The rebase - the dreaded rebase. What is a rebase? I use rebasing for a couple of different things so I looked up what it’s official purpose is:

‘Reapply commits on top of another base tip’ - [Git - git-rebase Documentation](https://git-scm.com/docs/git-rebase)

😐


So anyway, how I use git rebase.

Before raising a PR - I will usually rebase my branch onto master (stay with me) as this allows me to resolve conflicts through each of my commits. When I say rebase onto master I mean: git rebase master (make sure you have latest master) which will take my commits and apply them on top of the head of the master branch. Your base is your first commit on your branch which will come after whatever was the latest commit when you checked your branch out, and you are reapplying it as if you’ve just checked out from your base branch.

I also use rebase to rewrite history and there are a couple of ways I can do this:

Sometimes I spot something small - maybe a linter error that I want to add to an earlier commit. To do this, I will use git rebase interactive, my flow is something like:

Stash the change I want to apply
Start an interactive rebase `git rebase -i HEAD~3` 3 is the number of commits you want to go back
A text editor will open listing out your commits
On the commit you want to change, remove the keyword ‘pick’ and replace it with ‘edit’
Save and close that file
You will now be taken into a git delorean and all of a sudden be at a different point in your git history
Make the change you want to make
Save and amend the commit message if necessary
Hit git rebase —continue to fly back to the present



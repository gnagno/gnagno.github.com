---
layout: post
title: "Git stashing"
description: "Some useful tricks with git stash"
category: "git"
tags: [git, stash]
---
{% include JB/setup %}

Moving between different branches during my work I have discovered how useful git stash can be. The more I use it and the more tricks I read, the more confident I feel with it.

The stash is useful when you need to save your changes to a temporary place, move onto something else and then get back to your changes afterwards.

<!--more-->

## Adding your code changes to the stash

The basic command to stash your work is:

        git add .
        git stash

This adds your code modifications to the top of the stash.

## Listing your stashes

To see the list of stashed changes simply run:

        git stash list

this will return something like:

        stash@{0}: WIP on another-feature: fc92b1f initial commit
        stash@{1}: WIP on cool-feature: fc92b1f initial commit

Every stash is identified by the string 

        stash@{<number>}

The lower the number is in the braces, the more recent the stash is.

## Adding more information to the list

So you stashed your changes and saw the list, but let’s admit it, the list is a bit cryptic. What we need is something that allows us to apply a label. This can be achieved using the save parameter:

        git stash save "something meaningful"

Listing the stash again, we now have:

        stash@{0}: On another-cool-feature: something meaningful
        stash@{1}: WIP on another-feature: fc92b1f initial commit
        stash@{2}: WIP on cool-feature: fc92b1f initial commit

## What did I just save?

What happens when you want to get back your work but you don’t remember what you saved in your stash? Well… you can use the show command to see the changes in your stash:

        git stash show

And you will get a diff of the changes, by default this will show you a diff between your current working directory and the last stash. If you want to see the diff with an older stash e.g. stash@{2} you can do:

        git stash show stash@{2}

## Popping vs applying

Cool you saved your stash, and you saw what you saved, how can you re-apply the change you made?

There are two commands to do this, apply and pop, both will apply the stash to your code. Pop will delete the stash from the list, apply will leave it in place:

        git stash pop

And the last stash will be applied to your code. Again if you don’t want to apply the last stash, but an earlier one you can specify the stash id with:

        git stash pop stash@{2}

## Deleting stashes

When you start to use the stash more, your stashed list may get quite long. To delete a stash (for example the one identified by stash@{2}) you simply run:

        git stash drop stash@{2}

And stash@{2} will be gone forever!

If you want to delete everything in your stash use:

        git stash clear

## One more trick

Let’s suppose you want to create a new branch from your working branch and apply one of your stashes:

        git checkout original-branch
        git checkout -b my-new-beautiful-branch
        git stash pop stash@{0}

And you have a new my-new-beautiful-branch with the modifications from stash@{0}. You can join these two commands in one with:

        git stash create my-new-beautiful-branch stash@{0}

It’s interesting to note here that you can execute this command from any branch, the resulting branch (my-new-beautiful-branch) will always be a direct branch of original-branch. And if you omit the stash id, this command will use the most recent stashed change by default.

*Thats it, happy stashing!*

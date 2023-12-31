# Deleting Circles Kata

## The Problem

Relational databases natively support "cascade delete": in other words, if you delete an entity, its references in other parts of the database will be deleted too.

This is very helpful in more complex applications... like the one we have here.

How can we replicate this behaviour cleanly in pure frontend state?

This repo has an example animation-creation app which works like this:

- Circles are specified globally on the right panel.
- Keyframes, each of which is a canvas on which circles can be positioned, are specified in the timeline at the top and edited in the main view.
- We imagine there is a render button that interpolates the keyframes and produces a finished animation.

The app is not fully functional but enough of the state is implemented for the purposes of this kata, namely adding and deleting of the related entities.

## Your Mission

The app as implemented in `apps/redux` has an important issue. When a user deletes a shape from the global store (via the "Delete" button at the bottom of the disclosure on the right hand side), the app crashes. This is because the delete-shape reducer does not clean up references to that shape in the keyframes.

Your task: Fix the crash!

There are several considerations that form part of the challenge:

- The existing Redux architecture is not really designed for managed entity references between entities.
- There are no tests and the crash is a bit annoying to reproduce manually (requires several clicks).
- The app is a single package in a rather unnecessary monorepo (this is actually entirely accidental because I wanted to try turborepo, but now I'm doubling down and claiming it is part of the challenge).

When solving, consider what architectural patterns might make cascade-delete behaviour automatic in the context of this app.

## Starter Code

In `apps/redux` the app is implemented using just Redux and Redux Toolkit. This is your starting point.

You may wish to stick with Redux or migrate to an alternative state management framework.

## Credits

The repo structure was created with [Create Turbo](https://turbo.build/repo/docs/getting-started/create-new).

Much of the boilerplate for the frontend was generated by AI tools including:

- [Github Copilot](https://github.com/features/copilot)
- [Cursor.sh](https://cursor.sh/)
- [Claude.ai](https://claude.ai/)
- [v0](https://v0.dev)

Where UI generated using v0 it is marked as such in a comment and you can click through its link to see the original prompt and generation.

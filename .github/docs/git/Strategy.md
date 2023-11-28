# Git Strategy 🎫

We follow the [Github flow](https://githubflow.github.io/) strategy based on it's simplicity. The only difference is that our principal branch is called `main` instead of `master`.

**Table of Contents:**
- [Git Strategy 🎫](#git-strategy-)
- [Git Flow](#git-flow)
- [Development Flow 👨‍💻](#development-flow-)

# Git Flow

All the changes to the codebase must be reviewed by our peers before merging to the `main` branch.

We keep the `main` branch always `green` by ensuring the new changes don't break previous functionality.

# Development Flow 👨‍💻
We enforced some rules to protect our main branches. Some of them are:
1. At least 1 reviewer should approve our changes.
2. All conversations should be marked as closed.
3. All CI checks for that branch should pass.
4. Every change should be merged via PR.
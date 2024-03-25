# Argo CD / Rollouts Workshop 201

## 1. Prerequisites

Make sure all the prerequisites are met before starting the 201 workshop.

- [Prerequisites 201](201_prereqs.md) - Complete list of tools that need to be installed for this workshop

## 2. Advanced Argo CD exercises

- [Exercise 1](exercise-201/exercise1.md) - Configure Users permissions for Argo CD
- [Exercise 2](exercise-201/exercise2.md) - Create dynamic applications with ApplicationSets

## 3. Advanced Argo Rollouts exercises

- [Exercise 3](exercise-201/exercise3.md) - Performing a canary rollout with Istio
- [Exercise 4](exercise-201/exercise4.md) - Performing a canary rollout with analysis and auto rollback
- [Exercise 5](exercise-201/exercise5.md) - Performing a canary rollout with a traffic mirroring step
- [Exercise 6](exercise-201/exercise6.md) - Performing a canary rollout with a traffic header step

---

Here is a small walkthrough tutorial on how to use GitHub CLI (`gh`) to manage pull requests (PRs). This includes creating a PR, reviewing it, accepting the review, and merging it.

### Step 1: Create a New Branch and Make Some Changes

First, make sure you are on the main branch, then create a new branch.

```bash
git checkout main
git pull origin main
git checkout -b feature-branch
```

Make some changes to the code and commit them.

```bash
# Make some code changes here
git add .
git commit -m "Add new feature"
```

Push the changes to GitHub.

```bash
git push --set-upstream origin feature-branch
```

### Step 2: Create a Pull Request

To create a PR, you'll use the `gh pr create` command.

```bash
gh pr create -B main -H feature-branch -t "Add new feature" -b "This PR adds a new feature." -l "enhancement"
```

This will create a PR to merge `feature-branch` into `main` with the title "Add new feature" and the label "enhancement".

### Step 3: Review the Pull Request

To review the PR, first, list the available PRs.

```bash
gh pr list
```

You'll see a list of PRs. Use the PR number to review it.

```bash
gh pr review <PR_NUMBER> --comment -b "Looks good to me!"
```

This will add a comment "Looks good to me!" to the PR.

### Step 4: Accept the Review

To formally approve the PR:

```bash
gh pr review <PR_NUMBER> --approve # It important note that you cannot approve your own PR however you can merge it
```

This sets the review status to "Approved".

### Step 5: Switch to the Main Branch

It's advisable to switch back to the `main` branch before performing the merge. Here's the updated sequence:

```bash
git checkout main
git pull origin main
```

This ensures that your local `main` branch is up-to-date with the remote.

### Step 6: Merge the Pull Request

Now, you can merge the pull request. Replace `<PR_NUMBER>` with the actual number of the pull request.

```bash
gh pr merge <PR_NUMBER> --merge
```

This will merge the pull request into `main` using a merge commit. If you prefer, you can use `--rebase` or `--squash` as alternatives to `--merge`.

After this, you might want to pull the changes to your local `main` branch to make sure it's synchronized with the remote:

```bash
git pull origin main
```

Now your `main` branch both locally and remotely should include the changes you've merged.

### Step 7: Cleanup (Optional)

After the PR is successfully merged, you can delete the feature branch.

```bash
git branch -d feature-branch
git push origin --delete feature-branch
```

And there you go! You've just gone through the entire process of managing a PR using GitHub CLI.

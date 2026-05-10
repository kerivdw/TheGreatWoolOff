# The Great Wool-Off 🐑🦙

A low-stakes turf war between two teams - the **Alpacas** and the **Black Sheep** - designed to teach Git fundamentals through playful competition.

---

## What You'll Learn

By the end of this game you'll have practised:

- **Clone** - getting the repo onto your machine
- **Branch** - creating your own workspace
- **Commit** - saving your changes
- **Push** - sharing your branch with the team
- **Pull request (PR)** - proposing your changes for review
- **Resolve conflicts** - merging competing edits to the same file
- **Pull** - syncing the latest changes back to your machine

---

## Setup

1. Make sure Git is installed: `git --version`
2. Make sure you have a GitHub account and access to this repo
3. Configure your identity if you haven't already:
   ```
   git config --global user.name "Your Name"
   git config --global user.email "you@example.com"
   ```
4. Clone the repo:
   ```
   git clone https://github.com/kerivdw/TheGreatWoolOff.git
   cd TheGreatWoolOff
   ```

---

## How to Play

Follow these steps each round. Every player does this independently - that's how the conflicts happen.

### Step 1 - Pull the latest main

Before each round, make sure you're starting from the current state of the game:

```
git checkout main
git pull origin main
```

### Step 2 - Create your branch

Name your branch after yourself (or your character):

```
git checkout -b alpacas/round-1-felicity
```

Convention: `[team]/round-[number]-[your-name]`

### Step 3 - Create your competitor file

Copy the template and rename it to your character's name:

```
cp competitors/_template.md competitors/felicity-the-fabulous.md
```

Fill in your character's details. Be creative - this is your moment to shine.

### Step 4 - Edit the shared leaderboard

Open `leaderboard.md` and make your team's edits:

- Update the **Current Champion** line to claim your team's dominance
- Add your name to your team's **Standings** section
- Replace the **Latest insult** with something suitably dramatic
- Vote for your preferred snack
- Add an entry to the **Hall of Fame** if your team did something legendary

> This is the file where conflicts happen. Multiple people editing the same lines is the whole point.

### Step 5 - Stage and commit your changes

```
git add .
git commit -m "Round 1: Felicity claims the championship and updates standings"
```

Write a commit message that describes what you actually changed.

### Step 6 - Push your branch

```
git push origin alpacas/round-1-felicity
```

### Step 7 - Open a pull request

Go to the repo on GitHub and open a PR from your branch into `main`. Give it a title like:

> Round 1: Felicity's bold claim to the throne

### Step 8 - Resolve conflicts

If someone else merged their PR first, GitHub will tell you there's a conflict. This is expected - it's the whole game.

To resolve it:

```
git checkout main
git pull origin main
git checkout alpacas/round-1-felicity
git merge main
```

Git will mark the conflicting sections in the file. Open the file and look for conflict markers (see below). Decide what the merged result should look like, remove the markers, save, then:

```
git add leaderboard.md
git commit -m "Resolve merge conflict: kept Felicity's champion claim"
git push origin alpacas/round-1-felicity
```

Then update your PR on GitHub - it should now be mergeable.

---

## Conflict Markers - What They Look Like

When Git can't automatically merge two changes, it leaves markers in the file like this:

```
<<<<<<< HEAD
👑 Current Champion: Felicity the Fabulous (Alpacas)
=======
👑 Current Champion: Barry Baa-low (Black Sheep)
>>>>>>> main
```

- Everything between `<<<<<<<` and `=======` is **your version**
- Everything between `=======` and `>>>>>>>` is **the other version**
- Your job is to pick one, combine them, or write something new - then delete all three marker lines

The resolved result might look like:

```
👑 Current Champion: DISPUTED - Felicity vs Barry (outcome: TBD)
```

Or just pick a winner. You're in charge now.

---

## Rounds

### Round 1 - Basic Claims

**Goal:** Get comfortable with the full PR workflow.

Each player:
- Creates their competitor file
- Adds their name to the leaderboard standings
- Claims the championship on the champion line
- Opens a PR

First PR to merge wins Round 1. Everyone else resolves the conflict.

**What to practise:** branch, commit, push, PR, basic conflict resolution.

---

### Round 2 - The Comeback

**Goal:** Intentional conflicts on multiple lines.

Rules:
- Each player must edit **at least three different sections** of `leaderboard.md`
- You must counter the previous round's champion line with a better claim
- Add a comeback insult to the Latest Insult line

**What to practise:** resolving conflicts across multiple hunks in one file.

---

### Round 3 - Sabotage

**Goal:** Conflicts with actual decision-making.

Rules:
- Each player edits their **own competitor file** (easy, no conflict)
- But also edits another player's competitor file to "correct" their stats (conflict guaranteed)
- The Hall of Fame section must be reordered by each player

**What to practise:** three-way conflicts, keeping what matters and discarding what doesn't.

---

### Round 4 - The Peace Treaty

**Goal:** Collaborative conflict resolution.

Rules:
- Two players must pair up and intentionally resolve a conflict together
- The leaderboard must end Round 4 with **both teams listed in the standings**
- The champion line must name a joint winner

**What to practise:** communication during resolution, deliberate merging.

---

## Tips

- **Pull before you branch.** Stale starting points make conflicts worse.
- **Small commits are easier to review.** One logical change per commit.
- **Read the whole conflict before resolving it.** Don't just keep yours by default.
- **Commit messages explain the why.** "Fixed leaderboard" is less useful than "Claimed Round 2 victory after resolving conflict with Barry's edits".
- If you get stuck, `git status` is your friend - it tells you exactly what state you're in.
- To abandon a merge gone wrong: `git merge --abort`

---

## Glossary

| Term | What it means |
|---|---|
| **Repository (repo)** | The folder that contains the project and its full history |
| **Branch** | A parallel version of the repo where you make your changes |
| **Commit** | A saved snapshot of your changes, with a message describing them |
| **Push** | Sending your commits from your machine to GitHub |
| **Pull** | Bringing the latest commits from GitHub down to your machine |
| **Pull request (PR)** | A proposal to merge your branch into main, reviewed on GitHub |
| **Merge conflict** | What happens when two people edited the same part of a file differently |
| **HEAD** | Your current position in the repo - usually the tip of your branch |
| **Origin** | The default name for the remote (GitHub) copy of the repo |

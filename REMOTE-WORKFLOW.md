# Remote Workflow - Build from Anywhere

This lets you start on your laptop, then continue from your phone or any device.

---

## How It Works

1. **Planning phase** → Use Claude Code (works on laptop or in Codespaces)
2. **Build phase** → Runs in GitHub Codespaces (free cloud environment, accessible from phone browser)
3. **Notifications** → Get notifications when build completes or needs attention

---

## One-Time Setup (Do This Once)

Run the setup scripts:

```bash
cd /path/to/claude-build-workflow
./one-time-setup.sh      # Sets up GitHub template
./setup-notifications.sh  # Sets up phone notifications
```

This automatically:
- Creates a template repo on your GitHub
- Configures notifications

---

## Starting a New Project (Each Time)

### From Your Laptop or Phone:

#### Step 1: Create New Repository from Template
1. Go to github.com/YOUR-USERNAME/claude-build-template
2. Click "Use this template" → "Create a new repository"
3. Name it your project name (e.g., `my-cool-app`)
4. Click "Create repository"

#### Step 2: Open in Codespaces
1. On your new repo page, click the green "Code" button
2. Click "Codespaces" tab
3. Click "Create codespace on main"
4. Wait for it to load (takes ~1 minute)

#### Step 3: Install Claude Code in Codespaces
In the Codespaces terminal:
```bash
npm install -g @anthropic-ai/claude-code
claude auth login
```

#### Step 4: Run the Workflow
```bash
claude
```

Then say:
```
Run the workflow
```

#### Step 5: Do the Planning
Answer Claude's questions about what you're building. This is the interview/discovery phase.

#### Step 6: Start the Autonomous Build
When Claude says you're ready:
```bash
# Exit Claude
# Then run:
./ralph.sh
```

### Step 7: Close and Check Later
- You can close the browser - Codespaces keeps running for ~30 minutes of inactivity
- To keep it running longer, the build loop keeps it active
- Check back from any device by going to github.com/codespaces

---

## Checking Progress from Phone

### Option A: GitHub Codespaces (Full Control)
1. Open browser on phone
2. Go to github.com/codespaces
3. Click on your running codespace
4. You'll see the terminal with build progress
5. You can type commands, check files, etc.

### Option B: Quick Progress Check
If you just want to see status without opening Codespaces:
- Check the git commits in your repo (each completed story = 1 commit)
- Look at the commit messages to see what's done

---

## If Build Needs Attention

If something fails or needs input:
1. Open Codespaces from phone
2. Check the terminal for error messages
3. Check `progress.txt` for details: `cat progress.txt`
4. Fix the issue or update `prd.json` to skip the problematic story
5. Re-run: `./ralph.sh`

---

## Tips

- **Codespaces timeout**: Free tier stops after 30 min inactive, but the build loop counts as activity
- **Monthly limits**: Free tier has 60 hours/month - plenty for most projects
- **Save money**: Stop your codespace when not using it (it auto-stops anyway)
- **Commits are saved**: Even if codespace stops, your git commits are saved to GitHub

---

## Quick Reference

| Task | How |
|------|-----|
| Start new project | Use template → Create codespace → Run claude |
| Check progress | github.com/codespaces → open terminal |
| See what's done | Check repo commits |
| Resume build | Open codespace → `./ralph.sh` |
| Stop build | Open codespace → `Ctrl+C` |

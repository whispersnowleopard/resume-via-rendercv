# Resume Version Control Strategy

## Current Setup

**Main Branch** (`main`): Partner Development Manager focus (Anthropic, other partner roles)
**Technical Branch** (`business-systems-director`): Director of Business Systems / Functional Architect focus

## Git Workflow

### Initial Setup (do this once)

```bash
# Make sure your current Anthropic-focused version is committed
cd resume-via-rendercv
git add Dave_Gilbert_CV.yaml
git commit -m "Update for Partner Development Manager roles - emphasize partner ecosystem skills"

# Create the technical branch
git branch business-systems-director

# You're still on main - this is your Anthropic version
```

### When Applying for Partner Roles

```bash
# Make sure you're on main
git checkout main

# Make any tweaks
# Edit Dave_Gilbert_CV.yaml
git add Dave_Gilbert_CV.yaml
git commit -m "Customize for [Company] Partner Manager role"

# Generate resume
rendercv render Dave_Gilbert_CV.yaml
```

### When Applying for Technical Roles

```bash
# Switch to technical branch
git checkout business-systems-director

# First time: Make the technical skills changes
# Edit Dave_Gilbert_CV.yaml with detailed technical skills section
git add Dave_Gilbert_CV.yaml
git commit -m "Create Business Systems Director version with detailed technical skills"

# Generate resume
rendercv render Dave_Gilbert_CV.yaml

# Switch back to main when done
git checkout main
```

### Syncing Changes Between Branches

If you update your experience or education on one branch and want it on the other:

```bash
# Say you added a new job on main, and want it on business-systems-director
git checkout main
git add Dave_Gilbert_CV.yaml
git commit -m "Added new role at [Company]"

git checkout business-systems-director
git cherry-pick <commit-hash>  # Gets that one commit
# Or merge if you want all changes
git merge main  # Brings all main changes, may need to resolve conflicts in skills section
```

## The Two Skills Sections

### Main Branch (Partner Focused)
```yaml
skills:
  - label: Partner Management
    details: Ecosystem Development, Go-to-Market Strategy, Partner Enablement, Program Design & Scaling, Performance Analytics, Cross-Functional Collaboration
  - label: Business Systems
    details: Business Intelligence (Domo, NetSuite), ERP (NetSuite, SAP), Integration Platforms (MuleSoft, Boomi), CRM (NetSuite, Salesforce), Process Automation
  - label: Technical Background
    details: SuiteScript, Python, Data Modeling, System Architecture, Business Process Design
```

### Business Systems Director Branch (Technical Focused)
```yaml
skills:
  - label: Applications & Platforms
    details: DA/DV/BI (Domo, NetSuite, Python), ERP (NetSuite, SAP, Oracle, Great Plains), iPaaS (MuleSoft, Boomi), CRM (NetSuite, Salesforce), Marketing Automation (Marketo), FP&A (NetSuite Planning & Budgeting, Planful/Host Analytics)
  - label: Technical Capabilities
    details: Coding (SuiteScript, Python, JavaScript, HTML/CSS, Bash), Data Modeling, System Architecture, Functional Specifications (BRD/TRD), API Integration, Testing & Debugging, Change Management, Governance
  - label: Business Systems Leadership
    details: ERP Implementation, System Optimization & Scalability, Business Process Design & Redesign, Requirements Gathering, Cross-Functional Collaboration, Vendor Management
```

## Quick Reference

**Which branch am I on?**
```bash
git branch  # Shows all branches, * marks current
```

**See differences between branches**
```bash
git diff main business-systems-director Dave_Gilbert_CV.yaml
```

**List all commits on current branch**
```bash
git log --oneline
```

## Pro Tips

1. **Always commit before switching branches** - Git won't let you switch with uncommitted changes
2. **Use descriptive commit messages** - "Update for Anthropic application" not "changes"
3. **Push both branches to GitHub** - `git push origin main && git push origin business-systems-director`
4. **Keep experience/education in sync** - Those should be identical across branches, only skills/focus differs

## Emergency: "Oh shit I edited the wrong branch"

```bash
# Save your changes
git stash

# Switch to correct branch
git checkout correct-branch

# Apply your changes
git stash pop
```

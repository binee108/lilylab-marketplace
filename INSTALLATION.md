# LilyLab Marketplace - Installation Guide

> Complete guide to installing and configuring LilyLab Marketplace for individuals and teams

## 📋 Table of Contents

- [Prerequisites](#prerequisites)
- [Individual Installation](#individual-installation)
- [Team Installation](#team-installation)
- [Verification](#verification)
- [Troubleshooting](#troubleshooting)
- [Advanced Configuration](#advanced-configuration)

## Prerequisites

Before installing LilyLab Marketplace, ensure you have:

- ✅ Claude Code installed and running
- ✅ Git installed (for plugin updates)
- ✅ Internet connection (for marketplace access)
- ✅ Basic familiarity with command-line interfaces

### System Requirements

- **Claude Code**: Latest version recommended
- **Operating Systems**: macOS, Linux, Windows
- **Disk Space**: ~10MB per plugin
- **Network**: HTTPS access to GitHub

## Individual Installation

For solo developers who want to use LilyLab plugins on their local machine.

### Method 1: Interactive Installation (Recommended)

**Step 1: Start Claude Code**

```bash
claude
```

**Step 2: Add LilyLab Marketplace**

```bash
/plugin marketplace add binee108/lilylab-marketplace
```

You'll see:
```
✓ Successfully added marketplace: lilylab-marketplace
Found 1 plugin(s) available
```

**Step 3: Browse and Install Plugins**

```bash
/plugin
```

Select options:
1. Choose "Browse plugins"
2. Select "lilylab-marketplace"
3. Choose "nine-step-workflow"
4. Select "Install now"

**Step 4: Restart Claude Code**

```bash
exit
claude
```

**Step 5: Verify Installation**

```bash
/help
```

You should see new commands like:
- `/workflow-exec`
- `/workflow-resume`
- `/workflow-rollback`
- `/plugin-update`

### Method 2: Direct Command Installation

**Quick installation with a single command:**

```bash
# Start Claude Code
claude

# Add marketplace and install plugin
/plugin marketplace add binee108/lilylab-marketplace && /plugin install nine-step-workflow@lilylab-marketplace
```

### Method 3: Local Development Installation

For plugin developers or contributors:

**Step 1: Clone the Marketplace**

```bash
cd ~/Development  # or your preferred directory
git clone https://github.com/binee108/lilylab-marketplace.git
```

**Step 2: Add Local Marketplace**

```bash
claude
/plugin marketplace add ~/Development/lilylab-marketplace
```

**Step 3: Install Plugins**

```bash
/plugin install nine-step-workflow@lilylab-marketplace
```

## Team Installation

Configure automatic plugin installation for your entire team using repository-level settings.

### Setup for Team Leaders

**Step 1: Create Team Configuration**

In your project repository, create `.claude/settings.json`:

```bash
mkdir -p .claude
cat > .claude/settings.json << 'EOF'
{
  "plugins": {
    "marketplaces": [
      {
        "name": "lilylab-marketplace",
        "source": "binee108/lilylab-marketplace",
        "enabled": true,
        "autoUpdate": true
      }
    ],
    "installed": [
      {
        "name": "nine-step-workflow",
        "marketplace": "lilylab-marketplace",
        "version": "1.1.0",
        "enabled": true,
        "autoUpdate": true
      }
    ]
  },
  "workflow": {
    "enableAutoPlanning": true,
    "defaultModel": "sonnet",
    "qualityGates": {
      "requirePlanApproval": true,
      "requireCodeReview": true,
      "requireDocReview": true,
      "requireTestReview": true
    }
  }
}
EOF
```

**Step 2: Commit Configuration**

```bash
git add .claude/settings.json
git commit -m "Add LilyLab Marketplace team configuration"
git push origin main
```

**Step 3: Document for Team**

Add to your project README:

```markdown
## Development Setup

This project uses Claude Code with LilyLab plugins:

1. Install Claude Code: [Installation Guide](https://docs.claude.com)
2. Clone this repository
3. Open in Claude Code
4. **Trust the repository folder when prompted**
5. Plugins will install automatically

### Included Plugins
- Nine-Step Workflow: Production-ready development workflow
```

### Setup for Team Members

**Step 1: Clone Repository**

```bash
git clone https://github.com/your-org/your-project.git
cd your-project
```

**Step 2: Open in Claude Code**

```bash
claude
```

**Step 3: Trust the Repository**

When Claude Code prompts:
```
This repository contains Claude Code settings. Do you trust this folder?
```

Select: **"Yes, trust this folder"**

**Step 4: Automatic Installation**

Claude Code will automatically:
1. ✅ Add LilyLab Marketplace
2. ✅ Install Nine-Step Workflow plugin
3. ✅ Configure workflow settings
4. ✅ Enable all features

**Step 5: Verify**

```bash
/plugin
```

You should see:
```
✓ nine-step-workflow@lilylab-marketplace (v1.1.0) - Enabled
```

## Verification

### Verify Marketplace Installation

```bash
/plugin marketplace list
```

Expected output:
```
📦 Installed Marketplaces:

lilylab-marketplace (binee108/lilylab-marketplace)
  Status: Active
  Plugins: 1
  Last Updated: 2025-11-13
```

### Verify Plugin Installation

```bash
/plugin
```

Expected output:
```
📦 Installed Plugins:

nine-step-workflow@lilylab-marketplace (v1.1.0)
  Status: Enabled
  Commands: 4
  Agents: 12
  Skills: 18
```

### Verify Commands

```bash
/help
```

Look for these new commands:
```
Plugin Commands:
  /workflow-exec    - Execute 9-step workflow for feature or bug
  /workflow-resume  - Resume workflow from last step
  /workflow-rollback - Roll back to previous phase
  /plugin-update    - Check and apply plugin updates
```

### Test Plugin Functionality

```bash
# Test workflow execution
/workflow-exec "Add sample feature"

# Test plugin update
/plugin-update --check-only
```

## Troubleshooting

### Issue: Marketplace Not Found

**Problem**: Cannot add marketplace or "not found" error

**Solution**:
```bash
# Verify GitHub access
curl -I https://github.com/binee108/lilylab-marketplace

# Try HTTPS URL explicitly
/plugin marketplace add https://github.com/binee108/lilylab-marketplace

# Check network connection
ping github.com
```

### Issue: Plugin Installation Fails

**Problem**: Plugin won't install or shows errors

**Solution**:
```bash
# Check marketplace is added
/plugin marketplace list

# Refresh marketplace
/plugin marketplace update lilylab-marketplace

# Retry installation
/plugin install nine-step-workflow@lilylab-marketplace

# Check logs
claude --debug
```

### Issue: Commands Not Appearing

**Problem**: Installed but commands don't show in `/help`

**Solution**:
```bash
# Restart Claude Code
exit
claude

# Verify plugin is enabled
/plugin

# Enable if disabled
/plugin enable nine-step-workflow@lilylab-marketplace

# Check plugin status
/plugin show nine-step-workflow@lilylab-marketplace
```

### Issue: Auto-Update Not Working

**Problem**: Plugin doesn't check for updates

**Solution**:
```bash
# Manual update check
/plugin-update

# Check version configuration
cat ~/.claude/plugins/nine-step-workflow/.version.json

# Force update
/plugin-update --force

# Manual git pull
cd ~/.claude/plugins/nine-step-workflow
git pull origin main
```

### Issue: Permission Denied

**Problem**: Cannot install plugins or access directories

**Solution**:
```bash
# Check permissions
ls -la ~/.claude/plugins/

# Fix permissions (macOS/Linux)
chmod -R u+rw ~/.claude/plugins/

# Fix permissions (Windows)
icacls %USERPROFILE%\.claude\plugins /grant %USERNAME%:F /T
```

### Issue: Team Installation Not Working

**Problem**: Team members don't see automatic installation

**Solution**:

1. **Verify `.claude/settings.json` exists in repository**
   ```bash
   git ls-files .claude/settings.json
   ```

2. **Ensure team members trust the folder**
   - Must click "Yes" when prompted
   - Can manually trust: Claude Settings → Trusted Folders

3. **Check JSON syntax**
   ```bash
   cat .claude/settings.json | jq .
   ```

4. **Verify Git pull**
   ```bash
   git pull origin main
   ```

## Advanced Configuration

### Custom Marketplace Location

Use local or custom marketplace location:

```bash
# Local directory
/plugin marketplace add /path/to/custom-marketplace

# Private GitHub repository
/plugin marketplace add your-org/private-marketplace

# Specific branch
/plugin marketplace add binee108/lilylab-marketplace#develop
```

### Plugin Version Pinning

Pin specific plugin versions in team config:

```json
{
  "plugins": {
    "installed": [
      {
        "name": "nine-step-workflow",
        "marketplace": "lilylab-marketplace",
        "version": "1.1.0",
        "enabled": true,
        "autoUpdate": false
      }
    ]
  }
}
```

### Multiple Marketplaces

Add multiple marketplaces:

```json
{
  "plugins": {
    "marketplaces": [
      {
        "name": "lilylab-marketplace",
        "source": "binee108/lilylab-marketplace",
        "enabled": true
      },
      {
        "name": "company-internal",
        "source": "company-org/internal-plugins",
        "enabled": true
      }
    ]
  }
}
```

### Selective Plugin Installation

Install only specific plugins for different teams:

**For Development Team**:
```json
{
  "plugins": {
    "installed": [
      {
        "name": "nine-step-workflow",
        "marketplace": "lilylab-marketplace",
        "enabled": true
      }
    ]
  }
}
```

**For QA Team**:
```json
{
  "plugins": {
    "installed": [
      {
        "name": "nine-step-workflow",
        "marketplace": "lilylab-marketplace",
        "enabled": true,
        "config": {
          "enabledAgents": ["feature-tester", "test-reviewer", "code-reviewer"]
        }
      }
    ]
  }
}
```

### Environment-Specific Configuration

Different configs for dev/staging/production:

**`.claude/settings.dev.json`**:
```json
{
  "plugins": {
    "installed": [
      {
        "name": "nine-step-workflow",
        "marketplace": "lilylab-marketplace",
        "version": "latest"
      }
    ]
  }
}
```

**`.claude/settings.prod.json`**:
```json
{
  "plugins": {
    "installed": [
      {
        "name": "nine-step-workflow",
        "marketplace": "lilylab-marketplace",
        "version": "1.1.0"
      }
    ]
  }
}
```

## Next Steps

After successful installation:

1. **Read Plugin Documentation**: [Nine-Step Workflow Guide](https://github.com/binee108/nine-step-workflow-plugin)
2. **Try First Workflow**: `/workflow-exec "Add sample feature"`
3. **Explore Agents**: `/agents` to see available agents
4. **Check Skills**: Review installed skills in plugin documentation
5. **Configure Team**: Set up team-specific workflows

## Support

Need help with installation?

- **Documentation**: [LilyLab Marketplace](https://github.com/binee108/lilylab-marketplace)
- **Issues**: [Report Installation Issues](https://github.com/binee108/lilylab-marketplace/issues)
- **Email**: dev@lilylab.io

---

**Successfully installed? Start building with `/workflow-exec`!** 🚀

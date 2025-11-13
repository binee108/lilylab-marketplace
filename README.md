# LilyLab Marketplace

> Official Claude Code plugin marketplace for LilyLab's quantitative research and development workflows

[![Plugins](https://img.shields.io/badge/plugins-1-blue.svg)](https://github.com/binee108/lilylab-marketplace)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Maintained](https://img.shields.io/badge/Maintained-Yes-green.svg)](https://github.com/binee108/lilylab-marketplace)

## 🎯 Overview

LilyLab Marketplace is a curated collection of Claude Code plugins designed specifically for quantitative research teams and enterprise software development workflows. Our plugins enhance Claude Code with specialized agents, quality gates, and automated workflows.

## 📦 Available Plugins

### Nine-Step Workflow Plugin (v1.1.0) ⭐ Featured

**Production-ready development workflow with specialized agents and quality gates**

- **12 Specialized Agents**: Planning, review, implementation, testing, documentation
- **18 Reusable Skills**: Tag-based search, phase decomposition, risk assessment, and more
- **4 Essential Commands**: `/workflow-exec`, `/workflow-resume`, `/workflow-rollback`, `/plugin-update`
- **Quality Gates**: Multi-stage approval system for code, plans, docs, and tests
- **Git Worktree Integration**: Isolate feature development without branch chaos
- **Auto-Update System**: Keep plugin up-to-date with latest features

[View Plugin Documentation →](https://github.com/binee108/nine-step-workflow-plugin)

**Categories**: Workflow Management, Quality Assurance, Productivity Tools

**Keywords**: workflow, agents, quality-gates, git-worktree, code-review, testing

## 🚀 Quick Start

### For Individual Developers

#### 1. Add the LilyLab Marketplace

```bash
# Start Claude Code
claude

# Add LilyLab marketplace
/plugin marketplace add binee108/lilylab-marketplace
```

#### 2. Install Plugins

```bash
# Browse available plugins
/plugin

# Install Nine-Step Workflow
/plugin install nine-step-workflow@lilylab-marketplace
```

#### 3. Verify Installation

```bash
# Check installed plugins
/plugin

# View available commands
/help
```

### For Teams

Set up automatic plugin installation for your entire team:

#### 1. Create Team Configuration

Add this to your repository's `.claude/settings.json`:

```json
{
  "plugins": {
    "marketplaces": [
      {
        "name": "lilylab-marketplace",
        "source": "binee108/lilylab-marketplace",
        "enabled": true
      }
    ],
    "installed": [
      {
        "name": "nine-step-workflow",
        "marketplace": "lilylab-marketplace",
        "version": "1.1.0",
        "enabled": true
      }
    ]
  }
}
```

#### 2. Team Members Trust Repository

When team members open the repository in Claude Code and trust the folder:
1. LilyLab marketplace is automatically added
2. Nine-Step Workflow plugin is automatically installed
3. All features are ready to use immediately

#### 3. Keep Plugins Updated

```bash
# Check for updates
/plugin-update

# Update to latest version
/plugin-update
```

## 📚 Plugin Categories

### 🔄 Workflow Management
Tools for managing development workflows and processes:
- **Nine-Step Workflow**: Complete 9-step development lifecycle

### ✅ Quality Assurance
Plugins for code review, testing, and quality gates:
- **Nine-Step Workflow**: Multi-stage quality gates and review system

### ⚡ Productivity Tools
Tools to enhance development productivity:
- **Nine-Step Workflow**: Automated workflows and specialized agents

## 🎓 Usage Examples

### Example 1: Start a New Feature

```
User: I need to add user authentication to my app

Claude will:
1. Invoke project-planner agent to analyze requirements
2. Create detailed implementation plan with phases
3. Submit plan to plan-reviewer for validation
4. Request your approval before implementation
5. Execute complete 9-step workflow automatically
```

### Example 2: Fix a Bug

```
/workflow-exec "Fix race condition in order processing"

Claude will:
1. Investigate using tag-based-search skill
2. Plan fix approach with risk assessment
3. Get plan approval
4. Implement fix in git worktree
5. Run code review, documentation, and tests
6. Commit and merge after all quality gates pass
```

### Example 3: Resume Interrupted Work

```
/workflow-resume

Claude will:
1. Analyze .plan/ directory for active plans
2. Determine last completed step
3. Resume from next step automatically
4. Continue through remaining workflow stages
```

## 🛠️ Marketplace Management

### Add LilyLab Marketplace

```bash
# From GitHub repository
/plugin marketplace add binee108/lilylab-marketplace

# From local directory (for development)
/plugin marketplace add /path/to/lilylab-marketplace
```

### Update Marketplace

```bash
# Refresh plugin list
/plugin marketplace update lilylab-marketplace
```

### Remove Marketplace

```bash
# Remove marketplace (plugins remain installed)
/plugin marketplace remove lilylab-marketplace
```

## 🔧 Configuration Options

### Marketplace Configuration

The marketplace can be configured in `.claude/settings.json`:

```json
{
  "plugins": {
    "marketplaces": [
      {
        "name": "lilylab-marketplace",
        "source": "binee108/lilylab-marketplace",
        "enabled": true,
        "autoUpdate": true,
        "checkInterval": "7d"
      }
    ]
  }
}
```

### Plugin Configuration

Individual plugins can be configured:

```json
{
  "plugins": {
    "installed": [
      {
        "name": "nine-step-workflow",
        "marketplace": "lilylab-marketplace",
        "version": "1.1.0",
        "enabled": true,
        "autoUpdate": true
      }
    ]
  }
}
```

## 📊 Marketplace Statistics

- **Total Plugins**: 1
- **Active Installations**: Growing
- **Average Rating**: ⭐⭐⭐⭐⭐
- **Last Updated**: 2025-11-13
- **Maintenance Status**: Active

## 🤝 Contributing

We welcome contributions to the LilyLab Marketplace! Here's how you can contribute:

### Adding Your Plugin

1. **Create Your Plugin**: Follow [Claude Code plugin guidelines](https://docs.claude.com/ko/plugins)
2. **Test Locally**: Ensure your plugin works correctly
3. **Submit Plugin**: Create a pull request with:
   - Plugin source code or GitHub repository
   - Complete documentation
   - Version information
   - Keywords and categories

### Plugin Requirements

To be included in LilyLab Marketplace, plugins must:

- ✅ Follow Claude Code plugin standards
- ✅ Include comprehensive documentation
- ✅ Use semantic versioning
- ✅ Have clear README with examples
- ✅ Pass quality review
- ✅ Be maintained actively

### Submission Process

1. Fork the marketplace repository
2. Add your plugin to `marketplace.json`
3. Include plugin documentation in `plugins/` directory
4. Submit pull request with description
5. Wait for review and approval

## 🐛 Troubleshooting

### Marketplace Not Found

```bash
# Verify marketplace URL
/plugin marketplace list

# Try re-adding
/plugin marketplace remove lilylab-marketplace
/plugin marketplace add binee108/lilylab-marketplace
```

### Plugin Installation Fails

```bash
# Check marketplace is added
/plugin marketplace list

# Verify plugin name
/plugin

# Try specific version
/plugin install nine-step-workflow@lilylab-marketplace --version 1.1.0
```

### Plugin Not Loading

```bash
# Restart Claude Code
exit
claude

# Check plugin status
/plugin

# Enable if disabled
/plugin enable nine-step-workflow@lilylab-marketplace
```

### Update Issues

```bash
# Manual update
cd ~/.claude/plugins/nine-step-workflow
git pull origin main

# Or reinstall
/plugin uninstall nine-step-workflow@lilylab-marketplace
/plugin install nine-step-workflow@lilylab-marketplace
```

## 📞 Support

### Documentation
- [LilyLab Marketplace](https://github.com/binee108/lilylab-marketplace)
- [Nine-Step Workflow Plugin](https://github.com/binee108/nine-step-workflow-plugin)
- [Claude Code Plugins](https://docs.claude.com/ko/plugins)

### Issues & Feedback
- [Report Marketplace Issues](https://github.com/binee108/lilylab-marketplace/issues)
- [Report Plugin Issues](https://github.com/binee108/nine-step-workflow-plugin/issues)

### Community
- Email: dev@lilylab.io
- GitHub: [@binee108](https://github.com/binee108)

## 📄 License

This marketplace and all LilyLab plugins are licensed under the MIT License - see individual plugin LICENSE files for details.

## 🗺️ Roadmap

### v1.1.0 (Coming Soon)
- [ ] Additional workflow automation plugins
- [ ] Quantitative research tools
- [ ] Data analysis agents
- [ ] Backtesting framework integration

### v1.2.0
- [ ] Machine learning workflow plugins
- [ ] API integration tools
- [ ] Performance monitoring agents
- [ ] Risk management tools

### v2.0.0
- [ ] Advanced quantitative research suite
- [ ] Team collaboration features
- [ ] Custom agent marketplace
- [ ] Enterprise SSO integration

## 🌟 Featured Plugins

### Nine-Step Workflow Plugin ⭐

The cornerstone of LilyLab's development methodology. This plugin transforms Claude Code into a complete development team with systematic planning, implementation, review, testing, and deployment.

**Perfect for:**
- Enterprise software development
- Team-based projects
- Quality-critical applications
- Large feature implementations
- Production deployments

[Get Started →](https://github.com/binee108/nine-step-workflow-plugin)

## 🙏 Acknowledgments

- Built on Claude Code's powerful plugin system
- Inspired by production workflows at leading tech companies
- Community feedback shapes our development

---

**Made with ❤️ by LilyLab Team**

[Get Started](#quick-start) | [View Plugins](#available-plugins) | [Contributing](#contributing) | [Support](#support)

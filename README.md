# Claude Code Agents

Specialized agents for Claude Code that enhance development workflows through targeted expertise and orchestrated collaboration.

## Quick Start

```bash
# Clone the repository
git clone https://github.com/everwise/claude-code-agents.git
cd claude-code-agents

# Install agents in your Claude Code setup  
ln -sf $(pwd)/agents ~/.claude/torch-agents

# Verify installation
ls ~/.claude/torch-agents/
```

## Agent Architecture

The agents follow a hierarchical structure with orchestrational agents coordinating specialized capabilities:

```
├── ORCHESTRATIONAL AGENTS (workflow coordinators)
│   ├── feature-architect → 3-phase development planning
│   ├── jira-workitem-implementer → ticket to PR automation  
│   ├── pr-review-comment-resolver → systematic PR feedback
│   └── iterative-quality-fixer → quality gate enforcement
│
└── SPECIALIZED AGENTS (focused expertise)
    ├── debugger → error troubleshooting
    ├── code-quality-reviewer → production readiness
    ├── tdd-test-writer → test-driven development
    └── 7 other specialized agents
```

## Quick Reference

### Complex Development
- **New features/bugs**: `feature-architect`
- **Jira tickets**: `jira-workitem-implementer` 
- **Quality issues**: `iterative-quality-fixer`

### Code Review & Quality
- **PR feedback**: `pr-review-comment-resolver`
- **Code review**: `code-quality-reviewer`
- **Test creation**: `tdd-test-writer`

### Troubleshooting
- **Errors/failures**: `debugger`
- **Comment cleanup**: `pr-comment-validator`

## Documentation

📖 **[Complete documentation and usage guidelines →](agents/README.md)**

Individual agent specifications are in the `agents/` directory.
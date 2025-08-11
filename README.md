# Claude Code Agents

A collection of specialized agents for Claude Code with hierarchical orchestration patterns. Orchestrational agents coordinate complex workflows by delegating to specialized agents.

## Agent Hierarchy

```
meta-agent (creates new agents)
│
├── ORCHESTRATIONAL AGENTS (workflow coordinators)
│   ├── feature-architect (3-phase development)
│   ├── jira-workitem-implementer (ticket → PR)  
│   ├── pr-review-comment-resolver (PR feedback)
│   └── iterative-quality-fixer (quality enforcement)
│
└── SPECIALIZED AGENTS (focused capabilities)
    ├── debugger (troubleshooting)
    ├── code-quality-reviewer (production readiness)
    ├── code-comment-reviewer (comment quality)
    ├── tdd-test-writer (test-driven development)
    ├── jira-workitem-analyzer (ticket analysis)
    └── pr-comment-validator (comment relevance)
```

## When to Use Which Agent

### For Complex Development Tasks
- **`feature-architect`** → New features, complex bugs, architectural changes
- **`jira-workitem-implementer`** → Complete Jira ticket implementation (APL-1234)
- **`iterative-quality-fixer`** → Fix failing tests, lint errors, type issues

### For Code Quality & Review
- **`pr-review-comment-resolver`** → Address multiple PR review comments  
- **`code-quality-reviewer`** → Production-readiness assessment
- **`code-comment-reviewer`** → Comment quality and hamburger detection
- **`pr-comment-validator`** → Check comment relevance after changes

### For Development Practices
- **`tdd-test-writer`** → Test-driven development workflow
- **`debugger`** → Systematic error troubleshooting  
- **`jira-workitem-analyzer`** → Parse ticket requirements

### For Agent Management
- **`meta-agent`** → Create new Claude Code agents

## Key Delegation Patterns

**`jira-workitem-implementer`** orchestrates:
- `jira-workitem-analyzer` → ticket analysis
- `feature-architect` → complex planning  
- `tdd-test-writer` → test creation
- `iterative-quality-fixer` → quality enforcement
- `debugger` + `code-quality-reviewer` → issue resolution

**`iterative-quality-fixer`** leverages:
- `debugger` → failure analysis
- `code-quality-reviewer` → quality assessment  

**`pr-review-comment-resolver`** uses:
- `iterative-quality-fixer` → systematic comment resolution

## Documentation

See individual agent specifications in `agents/` directory for detailed capabilities and usage instructions.
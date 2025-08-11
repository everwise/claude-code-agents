# Claude Code Agents

This repository contains specialized agent configurations for Claude Code, designed to enhance development workflows through targeted expertise in specific domains.

## Installation

To use these agents, create symbolic links in your Claude Code agents directory:

```bash
# Link individual agents
ln -sf /path/to/this/repo/*.md ~/.claude/agents/

# Or link the entire directory
ln -sf /path/to/this/repo ~/.claude/agents/custom
```

## Agent Architecture

The agents follow a hierarchical architecture with specialized roles:

### Core Development Agents

**[feature-architect](feature-architect.md)** - *Development Planning & Implementation*
- Systematic feature development from analysis to implementation
- Handles complex technical problems requiring multi-step solutions
- Use for: new feature development, complex bug investigations, system-wide changes

**[tdd-test-writer](tdd-test-writer.md)** - *Test-Driven Development*
- Implements test-driven development methodology
- Writes comprehensive tests before implementation
- Use for: new feature development, bug fixes requiring test coverage

**[debugger](debugger.md)** - *Error Resolution*
- Specialized in debugging errors, test failures, and unexpected behavior
- Use proactively when encountering issues
- Use for: runtime errors, test failures, performance issues

### Code Quality & Review Agents

**[code-quality-reviewer](code-quality-reviewer.md)** - *Production Code Review*
- Objective, uncompromising code review focused on production readiness
- Provides critical analysis without sugar-coating feedback
- Use for: pre-deployment review, code quality assessment, refactoring guidance

**[code-comment-reviewer](code-comment-reviewer.md)** - *Comment Quality Assurance*
- Reviews code comment quality and relevance
- Detects hamburger comments and verifies comment accuracy
- Use for: code review, comment cleanup, documentation quality

**[iterative-quality-fixer](iterative-quality-fixer.md)** - *Systematic Quality Improvement*
- Executes fix-test-verify cycles until quality gates pass
- Integrates with debugger and code-quality-reviewer agents
- Use for: systematic code quality improvements, automated fixing cycles

### Pull Request Management

**[pr-review-comment-resolver](pr-review-comment-resolver.md)** - *PR Comment Resolution*
- Comprehensive PR review comment resolution specialist
- Categorizes and systematically addresses review feedback
- Use for: resolving PR feedback, systematic comment addressing

**[pr-comment-validator](pr-comment-validator.md)** - *PR Comment Relevance*
- Identifies outdated PR comments after code changes
- Helps maintain clean, relevant review conversations
- Use for: PR cleanup, identifying stale comments

### Jira Integration

**[jira-workitem-analyzer](jira-workitem-analyzer.md)** - *Ticket Analysis*
- Extracts and structures implementation requirements from Jira tickets
- Produces development-ready summaries from ticket details
- Use for: ticket analysis, requirement extraction

**[jira-workitem-implementer](jira-workitem-implementer.md)** - *End-to-End Implementation*
- Complete implementation specialist from ticket analysis through PR creation
- Handles branch creation, code changes, testing, and pull request submission
- Use for: full ticket implementation, end-to-end development workflows

### Information Management

**[information-consolidator](information-consolidator.md)** - *Content Organization*
- Consolidates scattered, redundant, or poorly organized information
- Restructures content while maintaining all key details
- Use for: documentation cleanup, information organization, content restructuring

**[meta-agent](meta-agent.md)** - *Agent Creation*
- Generates new Claude Code sub-agent configuration files
- Creates custom agents based on user requirements
- Use for: creating new specialized agents, extending agent capabilities

## Usage Guidelines

### Proactive Agent Usage
Some agents should be used proactively without explicit user requests:
- **code-quality-reviewer**: After writing significant code
- **debugger**: When encountering any errors or issues
- **iterative-quality-fixer**: For systematic quality improvements
- **pr-review-comment-resolver**: When PR has review comments
- **information-consolidator**: For scattered or redundant content
- **jira-workitem-analyzer**: When working with Jira tickets
- **code-comment-reviewer**: During code reviews or refactoring

### Agent Selection
Choose agents based on the task at hand:
- **Complex features**: Start with `feature-architect` or `tdd-test-writer`
- **Bug fixes**: Use `debugger` first, then `iterative-quality-fixer` if needed
- **Code review**: Use `code-quality-reviewer` for comprehensive analysis
- **PR management**: Use `pr-review-comment-resolver` for systematic feedback resolution
- **Jira workflows**: Use `jira-workitem-analyzer` then `jira-workitem-implementer`
- **Documentation**: Use `information-consolidator` for organization tasks

## Agent Colors

Agents are color-coded for easy identification:
- **Green**: Code quality and review agents
- **Blue**: Information and content management agents
- **Red**: Debugging and error resolution agents
- **Yellow**: Development and implementation agents
- **Purple**: Pull request and workflow management agents
- **Orange**: Integration and analysis agents

## Contributing

When adding new agents:
1. Follow the established agent architecture patterns
2. Include clear descriptions and usage examples
3. Specify appropriate tools and color coding
4. Document proactive usage guidelines where applicable
5. Update this README to include the new agent

## Best Practices

- Use agents proactively when their expertise matches the current task
- Combine agents for complex workflows (e.g., `jira-workitem-analyzer` + `jira-workitem-implementer`)
- Leverage specialized agents rather than general-purpose approaches
- Follow the hierarchical architecture when building development workflows
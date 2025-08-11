# Claude Code Agents - Technical Reference

Comprehensive documentation for specialized Claude Code agents with detailed capabilities, usage patterns, and orchestration workflows.

## Agent Architecture Overview

### Orchestrational vs Specialized Agents

**Orchestrational Agents** coordinate complex workflows by delegating to multiple specialized agents:
- Handle end-to-end processes
- Make strategic decisions about which specialized agents to use
- Manage multi-step workflows with quality gates
- Examples: `feature-architect`, `jira-workitem-implementer`, `pr-review-comment-resolver`

**Specialized Agents** provide focused expertise in specific domains:
- Single responsibility, deep expertise
- Called by orchestrational agents or used directly for targeted tasks
- Examples: `debugger`, `code-quality-reviewer`, `tdd-test-writer`

## Orchestrational Agents

These agents coordinate complex workflows and delegate to specialized agents:

### Development & Implementation

**[feature-architect](feature-architect.md)** - *3-Phase Development Planning*
- Systematic exploration → planning → implementation approach
- Handles complex technical problems requiring multi-step solutions
- **Use for**: New feature development, complex bug investigations, architectural changes
- **Delegates to**: `tdd-test-writer`, `debugger`, `code-quality-reviewer`

**[jira-workitem-implementer](jira-workitem-implementer.md)** - *Complete Ticket Implementation*
- End-to-end implementation from Jira ticket analysis through PR creation
- Handles branch creation, code changes, testing, review, and pull request submission
- **Use for**: Full ticket implementation, automated development workflows
- **Delegates to**: `jira-workitem-analyzer`, `feature-architect`, `tdd-test-writer`, `iterative-quality-fixer`

### Quality & Process Management

**[iterative-quality-fixer](iterative-quality-fixer.md)** - *Systematic Quality Enforcement*
- Executes fix-test-verify cycles until all quality gates pass
- Integrates with debugger and code-quality-reviewer for analysis
- **Use for**: Systematic code quality improvements, automated fixing cycles
- **Delegates to**: `debugger`, `code-quality-reviewer`

**[pr-review-comment-resolver](pr-review-comment-resolver.md)** - *Comprehensive PR Feedback Resolution*
- Fetches, categorizes, and systematically addresses PR review comments
- Uses iterative fixing methodology for complex resolution cycles
- **Use for**: Resolving PR feedback, systematic comment addressing
- **Delegates to**: `iterative-quality-fixer`

## Specialized Agents

These agents provide focused expertise in specific domains:

### Development & Testing

**[tdd-test-writer](tdd-test-writer.md)** - *Test-Driven Development*
- Implements test-driven development methodology
- Writes comprehensive tests before implementation
- **Use for**: New feature development, bug fixes requiring test coverage

**[debugger](debugger.md)** - *Error Resolution*
- Specialized in debugging errors, test failures, and unexpected behavior
- Use proactively when encountering issues
- **Use for**: Runtime errors, test failures, performance issues

### Code Quality & Review

**[code-quality-reviewer](code-quality-reviewer.md)** - *Production Code Review*
- Objective, uncompromising code review focused on production readiness
- Provides critical analysis without sugar-coating feedback
- **Use for**: Pre-deployment review, code quality assessment, refactoring guidance

**[code-comment-reviewer](code-comment-reviewer.md)** - *Comment Quality Assurance*
- Reviews code comment quality and relevance
- Detects hamburger comments and verifies comment accuracy
- **Use for**: Code review, comment cleanup, documentation quality

### Pull Request Management

**[pr-comment-validator](pr-comment-validator.md)** - *PR Comment Relevance*
- Identifies outdated PR comments after code changes
- Helps maintain clean, relevant review conversations
- **Use for**: PR cleanup, identifying stale comments

### Jira & Project Management

**[jira-workitem-analyzer](jira-workitem-analyzer.md)** - *Ticket Analysis*
- Extracts and structures implementation requirements from Jira tickets
- Produces development-ready summaries from ticket details
- **Use for**: Ticket analysis, requirement extraction

### Content & Information Management

**[information-consolidator](information-consolidator.md)** - *Content Organization*
- Consolidates scattered, redundant, or poorly organized information
- Restructures content while maintaining all key details
- **Use for**: Documentation cleanup, information organization, content restructuring

**[meta-agent](meta-agent.md)** - *Agent Creation*
- Generates new Claude Code sub-agent configuration files
- Creates custom agents based on user requirements
- **Use for**: Creating new specialized agents, extending agent capabilities

## Orchestration Patterns

### Key Delegation Workflows

**`jira-workitem-implementer` workflow**:
```
1. jira-workitem-analyzer → Parse ticket requirements
2. feature-architect → Complex planning & architecture  
3. tdd-test-writer → Test creation
4. iterative-quality-fixer → Quality enforcement
5. debugger + code-quality-reviewer → Issue resolution
```

**`iterative-quality-fixer` workflow**:
```
1. debugger → Analyze failures and errors
2. code-quality-reviewer → Quality assessment  
3. Iterative fix-test-verify cycles until success
```

**`pr-review-comment-resolver` workflow**:
```
1. Fetch and categorize PR review comments
2. iterative-quality-fixer → Systematic comment resolution
3. Quality verification and PR cleanup
```

## Usage Guidelines

### Proactive Agent Usage
These agents should be used proactively without explicit user requests:
- **`debugger`**: When encountering any errors or issues
- **`code-quality-reviewer`**: After writing significant code
- **`iterative-quality-fixer`**: For systematic quality improvements
- **`pr-review-comment-resolver`**: When PR has review comments
- **`information-consolidator`**: For scattered or redundant content
- **`jira-workitem-analyzer`**: When working with Jira tickets
- **`code-comment-reviewer`**: During code reviews or refactoring

### Agent Selection Strategy

**For Complex Development Tasks**:
- **New features/complex bugs**: Start with `feature-architect`
- **Jira ticket implementation**: Use `jira-workitem-implementer` for end-to-end automation
- **Quality issues**: Use `iterative-quality-fixer` for systematic resolution

**For Code Quality & Review**:
- **Production readiness**: Use `code-quality-reviewer` for uncompromising assessment
- **PR feedback resolution**: Use `pr-review-comment-resolver` for systematic addressing
- **Test coverage**: Start with `tdd-test-writer` before implementation

**For Troubleshooting & Maintenance**:
- **Errors/failures**: Use `debugger` for systematic troubleshooting
- **Outdated comments**: Use `pr-comment-validator` for cleanup
- **Documentation**: Use `information-consolidator` for organization

## Advanced Usage Patterns

### Workflow Orchestration Examples

**Complex Feature Development**:
```bash
# 1. Start with architecture planning
feature-architect "implement user authentication system"

# 2. Test-driven approach
tdd-test-writer "write tests for authentication flow"  

# 3. Quality enforcement during development
iterative-quality-fixer "ensure all tests pass and code quality gates"
```

**Jira Ticket Resolution**:
```bash
# Single command for complete implementation
jira-workitem-implementer "APL-1234"

# Or step-by-step approach
jira-workitem-analyzer "APL-1234"
feature-architect "implement requirements from analysis"
```

**PR Review Workflow**:
```bash
# Address all review comments systematically
pr-review-comment-resolver "PR #123"

# Clean up outdated comments after changes
pr-comment-validator "PR #123"
```

### Agent Combination Strategies

**High-Quality Development**:
1. `tdd-test-writer` → Write tests first
2. `feature-architect` → Plan implementation  
3. `code-quality-reviewer` → Review code quality
4. `iterative-quality-fixer` → Fix any issues

**Emergency Bug Fix**:
1. `debugger` → Identify root cause
2. `tdd-test-writer` → Add regression tests
3. `iterative-quality-fixer` → Ensure fix is complete

## Technical Specifications

### Agent Color Coding
- 🟢 **Green**: Code quality and review (`code-quality-reviewer`, `code-comment-reviewer`, `iterative-quality-fixer`)
- 🔵 **Blue**: Information management (`information-consolidator`, `meta-agent`)
- 🔴 **Red**: Debugging and error resolution (`debugger`)
- 🟡 **Yellow**: Development and implementation (`feature-architect`, `tdd-test-writer`)
- 🟣 **Purple**: Pull request management (`pr-review-comment-resolver`, `pr-comment-validator`)
- 🟠 **Orange**: Integration and analysis (`jira-workitem-analyzer`, `jira-workitem-implementer`)

### Tool Access Patterns
- **Full Tools** (`*`): Orchestrational agents for maximum flexibility
- **Specialized Tools**: Focused tool sets for specialized agents
- **Read-Only**: Analysis agents with limited modification capabilities

## Development Guidelines

### Creating New Agents
1. **Define clear scope**: Single responsibility or orchestrational coordination
2. **Specify tool requirements**: Minimal necessary tool set
3. **Document delegation patterns**: If orchestrational, specify which agents to call
4. **Provide usage examples**: Clear scenarios for when to use the agent
5. **Color coding**: Follow established color patterns
6. **Proactive guidelines**: Specify if agent should be used proactively

### Agent Integration Best Practices
- **Favor orchestration over duplication**: Use existing specialized agents
- **Maintain clear boundaries**: Each agent should have distinct expertise
- **Document interdependencies**: Clear delegation and workflow patterns
- **Test agent interactions**: Ensure orchestrational workflows function correctly
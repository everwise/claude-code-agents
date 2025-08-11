# Claude Code Agents - Quick Reference

Specialized Claude Code agents for development workflows, quality assurance, and project management.

## Architecture

**Orchestrational Agents** - Coordinate complex workflows by delegating to specialized agents  
**Specialized Agents** - Provide focused domain expertise

## Orchestrational Agents

### **[feature-architect](feature-architect.md)** - 3-Phase Development Planning
- Exploration → planning → implementation for complex technical problems
- **Use for:** New features, complex bugs, architectural changes
- **Delegates to:** `tdd-test-writer`, `debugger`, `code-quality-reviewer`

### **[jira-workitem-implementer](jira-workitem-implementer.md)** - Complete Ticket Implementation  
- End-to-end: ticket analysis → implementation → PR creation
- **Use for:** Full ticket automation, development workflows
- **Delegates to:** `jira-workitem-analyzer`, `feature-architect`, `tdd-test-writer`, `iterative-quality-fixer`

### **[iterative-quality-fixer](iterative-quality-fixer.md)** - Systematic Quality Enforcement
- Fix-test-verify cycles until all quality gates pass
- **Use for:** Code quality improvements, automated fixing cycles  
- **Delegates to:** `debugger`, `code-quality-reviewer`

### **[pr-review-comment-resolver](pr-review-comment-resolver.md)** - PR Feedback Resolution
- Fetches, categorizes, and addresses PR review comments systematically
- **Use for:** PR feedback resolution, comment addressing
- **Delegates to:** `iterative-quality-fixer`

## Specialized Agents

### Development & Testing
**[tdd-test-writer](tdd-test-writer.md)** - Test-driven development, writes tests before implementation  
**[debugger](debugger.md)** - Error resolution, runtime issues, test failures

### Code Quality & Review  
**[code-quality-reviewer](code-quality-reviewer.md)** - Production-ready code review, critical analysis  
**[code-comment-reviewer](code-comment-reviewer.md)** - Comment quality, detects outdated comments

### Project Management
**[jira-workitem-analyzer](jira-workitem-analyzer.md)** - Ticket analysis, requirement extraction  
**[pr-comment-validator](pr-comment-validator.md)** - Identifies outdated PR comments

### Content Management
**[information-consolidator](information-consolidator.md)** - Consolidates scattered/redundant information  
**[meta-agent](meta-agent.md)** - Creates new agent configuration files

## Quick Workflows

**Jira Implementation:**
```
jira-workitem-analyzer → feature-architect → tdd-test-writer → iterative-quality-fixer
```

**Quality Enforcement:**  
```
debugger → code-quality-reviewer → iterative fix-test-verify cycles
```

**PR Resolution:**
```
Fetch PR comments → iterative-quality-fixer → quality verification
```

## Agent Selection Guide

**Complex Development:** `feature-architect` or `jira-workitem-implementer`  
**Quality Issues:** `iterative-quality-fixer` for systematic resolution  
**Testing:** `tdd-test-writer` before implementation  
**Errors:** `debugger` for systematic troubleshooting  
**PR Feedback:** `pr-review-comment-resolver` for systematic addressing  
**Documentation:** `information-consolidator` for organization

## Proactive Usage
Use these agents automatically without explicit requests:
- `debugger` - Any errors or issues
- `code-quality-reviewer` - After writing significant code  
- `iterative-quality-fixer` - Quality improvements
- `jira-workitem-analyzer` - Working with Jira tickets
- `information-consolidator` - Scattered/redundant content

## Technical Specs

### Color Coding
- 🟢 **Green:** Code quality (`code-quality-reviewer`, `code-comment-reviewer`, `iterative-quality-fixer`)
- 🔵 **Blue:** Information management (`information-consolidator`, `meta-agent`) 
- 🔴 **Red:** Debugging (`debugger`)
- 🟡 **Yellow:** Development (`feature-architect`, `tdd-test-writer`)
- 🟣 **Purple:** PR management (`pr-review-comment-resolver`, `pr-comment-validator`)
- 🟠 **Orange:** Integration (`jira-workitem-analyzer`, `jira-workitem-implementer`)

### Tool Access
- **Full Tools (*):** Orchestrational agents
- **Specialized Tools:** Domain-focused agents  
- **Read-Only:** Analysis agents

## Usage Examples

**Complete Feature Development:**
```bash
jira-workitem-implementer "APL-1234"  # End-to-end automation
```

**Step-by-Step Development:**
```bash
feature-architect "implement authentication system"
tdd-test-writer "write authentication tests"  
iterative-quality-fixer "ensure quality gates pass"
```

**PR Workflow:**
```bash
pr-review-comment-resolver "PR #123"  # Address all comments
pr-comment-validator "PR #123"       # Clean outdated comments
```
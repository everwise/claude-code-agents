# Iterative Fixing Patterns for Claude Code Agents

## Overview

This document defines standard patterns for implementing systematic iterative fixing capabilities across Claude Code agents. These patterns ensure consistent, reliable, and efficient resolution of code quality issues through structured fix-test-verify cycles.

## Core Architecture

### Agent Hierarchy
```
Primary Agent (e.g., jira-workitem-implementer, pr-review-comment-resolver)
├── iterative-quality-fixer (systematic fixing coordinator)
│   ├── debugger (failure analysis specialist)
│   └── code-quality-reviewer (quality assessment specialist)
└── Domain-specific logic
```

### Key Principles

1. **Single Responsibility**: Each agent has a focused purpose in the fixing ecosystem
2. **Systematic Iteration**: All fixing follows structured cycles with clear success criteria
3. **Evidence-Based Analysis**: All fixes are based on concrete debugging insights, not assumptions
4. **Graceful Degradation**: Partial success is handled gracefully with clear reporting
5. **Agent Composition**: Complex workflows compose specialized agents rather than reimplementing logic

## Standard Integration Patterns

### Pattern 1: Quality Gate Enforcement

**Use Case**: Ensuring code passes tests, linting, and type checking before completion

**Implementation**:
```markdown
- Delegate to `iterative-quality-fixer` sub-agent for comprehensive quality enforcement:
  - Handles systematic fix-test-verify cycles until all quality gates pass
  - Automatically runs lint, typecheck, and test verification 
  - Integrates with debugger agent for failure analysis and systematic resolution
  - Continues iteration until success or maximum attempts reached
```

**Agent Integration Points**:
- Replace manual quality gate execution with `iterative-quality-fixer` delegation
- Specify project scope, quality gates, and iteration limits
- Capture fix reports for broader workflow documentation

### Pattern 2: Failure Recovery Integration

**Use Case**: Handling unexpected errors during implementation or testing

**Implementation**:
```markdown
### Debugging Integration
- **Automated Quality Issues**: `iterative-quality-fixer` sub-agent automatically handles:
  - Test failures through systematic debugging cycles
  - Linting and type checking errors with iterative resolution
  - Integration with debugger agent for root cause analysis
  - Continuous fix-test-verify loops until resolution or maximum attempts

- **Implementation Errors**: Delegate to `debugger` agent for systematic troubleshooting:
  - Use ultrathink methodology for complex debugging scenarios
  - Apply systematic debugging approach for unexpected failures
  - Use debugging insights to refine implementation approach
```

**Agent Integration Points**:
- Clear separation between automated quality fixes and manual debugging needs
- Structured escalation from automated fixes to manual analysis
- Context preservation across debugging cycles

### Pattern 3: Comment/Review Resolution

**Use Case**: Systematically addressing feedback from code reviews or automated tools

**Implementation**:
```markdown
- **Parse and Categorize**: Identify specific actionable items
- **Prioritize by Severity**: Critical → High → Medium → Low
- **Delegate Resolution**: Use `iterative-quality-fixer` for systematic fixing
- **Track Progress**: Maintain detailed resolution status
- **Report Results**: Comprehensive summary with remaining manual items
```

**Agent Integration Points**:
- Comment parsing and categorization logic in primary agent
- Delegation to `iterative-quality-fixer` for systematic resolution
- Progress tracking and reporting coordination

## Implementation Guidelines

### For Primary Agents

**Quality Gate Integration**:
1. Replace manual quality commands with `iterative-quality-fixer` delegation
2. Specify clear success criteria and iteration limits
3. Handle both successful resolution and partial success scenarios
4. Document any remaining manual intervention requirements

**Error Handling Enhancement**:
1. Distinguish between automated fixable issues and manual debugging needs
2. Provide clear escalation paths from automated to manual resolution
3. Maintain context across debugging and fixing cycles
4. Document learnings for future similar scenarios

**Reporting Requirements**:
1. Include fix iteration history in agent reports
2. Document specific fixes applied and reasoning
3. Clearly identify remaining manual tasks
4. Provide performance metrics (iterations used, time taken)

### For Sub-Agent Development

**Systematic Iteration Logic**:
1. Implement clear iteration counting and limits
2. Track progress across cycles to avoid infinite loops
3. Apply evidence-based fixes from debugging analysis
4. Provide detailed iteration history in reports

**Agent Integration Points**:
1. Clear delegation patterns to debugger agent
2. Structured input/output interfaces for primary agents
3. Consistent reporting formats across all sub-agents
4. Graceful handling of edge cases and failures

**Quality Standards**:
1. Follow established testing patterns (MSW, vitest, React Testing Library)
2. Respect project conventions and architectural decisions
3. Ensure all fixes maintain existing functionality
4. Apply DRY, KISS, and Single Responsibility principles

## Adoption Checklist

### For Existing Agents

- [ ] Identify manual quality gate execution points
- [ ] Replace with `iterative-quality-fixer` delegation patterns
- [ ] Update error handling sections to include systematic fixing
- [ ] Enhance reporting to include fix iteration details
- [ ] Document any agent-specific customizations needed

### For New Agents

- [ ] Plan systematic fixing requirements during design phase
- [ ] Include `iterative-quality-fixer` integration points in workflow
- [ ] Design clear delegation patterns for debugging scenarios
- [ ] Implement comprehensive reporting with fix details
- [ ] Follow established agent composition patterns

## Common Anti-Patterns to Avoid

### ❌ Manual Quality Gate Implementation
```markdown
- Run `yarn nx test <project>`
- Run `yarn nx lint <project>`  
- Run `yarn nx typecheck <project>`
```

### ✅ Systematic Quality Gate Delegation
```markdown
- Delegate to `iterative-quality-fixer` sub-agent for comprehensive quality enforcement
```

### ❌ Ad-hoc Debugging Approaches
```markdown
- Try to fix the error manually
- Guess at potential solutions
- Make multiple changes without verification
```

### ✅ Systematic Debugging Integration
```markdown
- Delegate to `debugger` agent for systematic troubleshooting
- Apply evidence-based fixes from debugging recommendations
- Verify fixes through re-running quality gates
```

### ❌ Incomplete Error Handling
```markdown
- If tests fail, try to fix them
- Continue with next step regardless of failures
```

### ✅ Comprehensive Error Recovery
```markdown
- **Automated Quality Issues**: Use `iterative-quality-fixer` for systematic resolution
- **Implementation Errors**: Delegate to `debugger` agent with ultrathink methodology
- **Iterative Fixing Patterns**: Follow established systematic approach
```

## Performance Considerations

### Iteration Limits
- Default maximum iterations: 5 cycles
- Configurable based on complexity and time constraints
- Clear reporting when limits are reached

### Timeout Management
- Track time spent per iteration cycle
- Implement exponential backoff for persistent failures
- Graceful handling of long-running fix cycles

### Resource Efficiency
- Skip redundant quality gate execution when possible
- Cache debugging analysis results within iteration cycles
- Batch related fixes to minimize test execution overhead

## Future Enhancements

### Planned Improvements
- Machine learning integration for fix pattern recognition
- Cross-project fix knowledge sharing
- Automated iteration limit optimization based on historical data
- Integration with CI/CD systems for continuous quality enforcement

### Extension Points
- Custom quality gate definitions for specialized projects
- Domain-specific fixing strategies (security, performance, accessibility)
- Integration with external code analysis tools
- Automated fix suggestion generation for common patterns

---

## Usage Examples

### Basic Quality Enforcement
```markdown
Use the iterative-quality-fixer subagent to resolve all quality issues in the matching library.
```

### Targeted Fix with Limits
```markdown
Delegate to iterative-quality-fixer subagent for test failures only, maximum 3 iterations.
```

### PR Review Resolution
```markdown
Use the pr-review-comment-resolver agent to address all review comments from the last hour.
```

This document serves as the authoritative guide for implementing systematic iterative fixing patterns across the Claude Code agent ecosystem.
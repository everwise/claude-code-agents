# Commands

Custom Claude Code commands for streamlined workflows.

## Available Commands

- **pr-refresh-summary** - refresh PR summary to comprehensively reflect all current changes while preserving template structure
- **pr-gemini-review** - comment "@gemini-code-assist review" on the current PR

## Usage

Commands are automatically available in Claude Code when properly linked via `ln -sf $(pwd)/commands ~/.claude/commands/torch`.
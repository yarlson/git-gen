# 🧩 Git Plugins Collection: AI-Powered Git Tools

A collection of Git plugins leveraging Anthropic's Claude AI for better development workflows.

## Available Plugins

### 1. git-gen: Commit Message Generator

Generates meaningful commit messages by analyzing your changes.

### 2. git-ch: Changelog Generator

Generates changelogs between git tags with structured formatting.

## Installation

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/yarlson/git-gen.git
   ```

2. **Make the Scripts Executable**:

   ```bash
   chmod +x git-gen git-ch
   ```

3. **Create Symbolic Links**:
   ```bash
   sudo ln -s "$(pwd)/git-gen" /usr/local/bin/git-gen
   sudo ln -s "$(pwd)/git-ch" /usr/local/bin/git-ch
   ```

## Requirements

- `git`: Version control system
- `jq`: Command-line JSON processor
- `curl`: Data transfer tool
- Anthropic API key

## Configuration

### Setting up the API Key

Both plugins require an Anthropic API key set as an environment variable:

```bash
export ANTHROPIC_API_KEY='your_api_key_here'
```

For persistence, add it to your shell configuration file:

```bash
echo 'export ANTHROPIC_API_KEY="your_api_key_here"' >> ~/.bashrc
# or
echo 'export ANTHROPIC_API_KEY="your_api_key_here"' >> ~/.zshrc
```

**Security Note:** Consider the security implications of storing API keys in configuration files, especially on shared systems.

## Usage

### git-gen: Commit Message Generator

Generate and commit changes with AI-powered commit messages:

```bash
git gen                     # Generate message based on changes
git gen "purpose details"   # Optional: Provide context if purpose isn't clear from the changes
```

The plugin will:

1. Stage changes (`git add .`)
2. Analyze the repository state
3. Generate a commit message
4. Prompt for action:
   - `y` - accept and commit
   - `n` - generate new message
   - `e` - edit in $EDITOR

#### Commit Message Style

Generated messages follow these principles:

- Uses conventional commit format (e.g., `feat`, `fix`, `refactor`)
- Includes scope when relevant (e.g., `feat(auth)`, `fix(api)`)
- Provides specific details about changes
- Mentions the impact or improvement
- Maintains consistency with your repository's commit history

Example messages:

```
feat(api): implement rate limiting to handle 10k requests/min
fix(cache): resolve memory leak by adding LRU eviction
refactor(auth): extract JWT validation into middleware for better testing
```

### git-ch: Changelog Generator

Generate changelogs between git tags:

```bash
git ch > CHANGELOG.md    # Generate changelog between last two tags
```

The plugin will:

1. Find the last two tags in your repository
2. Analyze commits and changes between tags
3. Generate a structured changelog with:
   - Breaking changes
   - New features
   - Improvements
   - Bug fixes
4. List all commits with their hashes

#### Changelog Format

Generated changelogs follow this structure:

```markdown
# Version X.Y.Z

### Breaking Changes

- Changed authentication flow to OAuth2-only, requiring API key migration

### Features

- Added metrics collection API with Prometheus integration

### Improvements

- Updated Redis client to v7.2.0 for improved stability
- Updated several dependencies for security and performance

### Bug Fixes

- Fixed race condition in concurrent job processing

## Commits

- f8dcafd3e359856f36bc8e06df7d45c21a409c5e feat(cli): add version command
- e300a1edd86ef7dfb9ae7d606c32dec6fc3bff05 chore(deps): update dependencies
```

## Contributing

Contributions are welcome! Feel free to submit issues or pull requests on the repository.

## License

This project is licensed under the MIT License. See [LICENSE.md](LICENSE.md) for details.

## Security

- Keep your Anthropic API key secure
- Review generated content before using it
- Ensure you comply with Anthropic's terms of service and use case policies

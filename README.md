# 🧩 Git-Gen: AI-Powered Git Commit Message Generator

## Overview

`git-gen` is a Git plugin that automates the generation of meaningful commit messages using Anthropic's Claude AI model. It analyzes your repository changes and suggests concise, descriptive commit messages following best practices and conventional commit formats.

## Features

- Generates commit messages by analyzing git diff and staged changes
- Analyzes repository commit history for consistency
- Interactive commit message selection and editing
- Follows Conventional Commits specification
- Optional: Accepts user input when change purpose needs clarification

## Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yarlson/git-gen.git
   ```

2. **Make the Script Executable**:
   ```bash
   chmod +x git-gen
   ```

3. **Add to PATH**:
   ```bash
   mv git-gen /usr/local/bin
   ```

## Usage

Within any Git repository:

```bash
git gen                     # Generate message based on changes
git gen "purpose details"   # Optional: Provide context if purpose isn't clear from the changes
```

The script:
1. Stages changes (`git add .`)
2. Analyzes the repository state
3. Generates a commit message
4. Prompts for action:
   - `y` - accept and commit
   - `n` - generate new message
   - `e` - edit in $EDITOR

## Requirements

- `git`: Version control system
- `jq`: Command-line JSON processor
- `curl`: Data transfer tool
- Anthropic API key

## Configuration

### Setting up the API Key

The script requires an Anthropic API key set as an environment variable:

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

## Commit Message Style

The generator follows these principles:

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

## Contributing

Contributions are welcome! Feel free to submit issues or pull requests on the repository.

## License

This project is licensed under the MIT License. See [LICENSE.md](LICENSE.md) for details.

## Security

- Keep your Anthropic API key secure
- Review generated commit messages before accepting them
- Ensure you comply with Anthropic's terms of service and use case policies

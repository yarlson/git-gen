# 🧩 Git-Gen: Automated Git Commit Message Generator

## Overview

`git-gen` is a bash script that acts as a Git plugin to automate the generation of commit messages. It uses Anthropic's Claude model to analyze the changes in your Git repository and suggests a concise, informative commit message. The script also includes functionality to automatically prepend a Jira ticket ID to the commit message if it's present in the branch name.

## Features

- **Automatic Commit Message Generation**: Leverages Claude to generate commit messages based on the changes made.
- **Jira Ticket ID Detection**: Automatically detects and prepends Jira ticket ID from the branch name to the commit message.
- **Editable Commit Messages**: Offers the option to edit the generated commit message before committing.

## Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yarlson/git-gen.git
   ```
2. **Make the Script Executable**:
   Navigate to the script's directory and run:
   ```bash
   chmod +x git-gen
   ```
3. **Add to PATH**:
   For macOS/Linux, you can move the script to `/usr/local/bin` or another directory in your PATH:
   ```bash
   mv git-gen /usr/local/bin
   ```

## Usage

Once installed, you can use `git-gen` within any Git repository:

```bash
git gen
```

The script will perform the following actions:

- Analyze the current Git repository for changes.
- Generate a commit message using Anthropic's Claude.- Prompt you to accept (`y`), reject (`n`), or edit (`e`) the generated message.
- If the branch name contains a Jira ticket ID (like `DXP-123`), it will prepend this ID to your commit message.
- Commit the changes with the generated or modified commit message.

## Requirements

- `jq`: A lightweight and flexible command-line JSON processor.
- `curl`: A tool to transfer data from or to a server.
- `git`: Version control system.
- An active Anthropic API key set in your environment as ANTHROPIC_API_KEY.

## Configuration and Environment Variables

### ANTHROPIC_API_KEY

`git-gen` requires an Anthropic API key to generate commit messages using Claude. You need to set this key as an environment variable named `ANTHROPIC_API_KEY`. There are two common methods to do this:

1. **Exporting Temporarily**:
   You can export the API key in your current shell session. This method is temporary, and the API key will need to be re-exported in each new shell session.

   ```bash
   export ANTHROPIC_API_KEY='your_api_key_here'
   ```

2. **Adding to Shell Configuration**:
   For convenience, you might want to add the API key to your shell configuration file (like `.bashrc` or `.zshrc`). This method makes the API key persistently available in all future shell sessions.

   ```bash
   echo 'export ANTHROPIC_API_KEY="your_api_key_here"' >> ~/.bashrc
   # or
   echo 'export ANTHROPIC_API_KEY="your_api_key_here"' >> ~/.zshrc
   ```

   After adding it, reload your shell configuration with `source ~/.bashrc` or `source ~/.zshrc`, or simply restart your terminal.

   **Note:** While adding the API key to your shell configuration file is convenient, it may be considered less secure, especially on shared systems. It is important to understand the security implications of storing sensitive information like API keys in configuration files.

### Customizing the Script

You can further customize the behavior of `git-gen` by editing the script. For example, you might want to change the text editor used for editing commit messages or adjust the regular expression used for Jira ticket detection.

## Contributing

Contributions to `git-gen` are welcome! Please feel free to submit pull requests or raise issues on the repository.

## License

`git-gen` is licensed under the MIT License. See [LICENSE.md](LICENSE.md) for more information.

## Disclaimer

This script uses the Anthropic API to generate commit messages. Please ensure you comply with Anthropic's use case policies and have a valid API key.

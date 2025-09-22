# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an Ansible Hello World demonstration project that showcases Infrastructure as Code (IaC) best practices with comprehensive CI/CD automation. The main component is a simple Ansible playbook (`hello.yml`) that runs on localhost.

## Essential Commands

### Ansible Operations
```bash
# Run the main playbook
ansible-playbook hello.yml

# Syntax validation
ansible-playbook --syntax-check hello.yml

# Dry run (check mode)
ansible-playbook --check hello.yml
```

### Verification process
```bash
yamllint hello.yml
ansible-lint hello.yml
ansible-playbook --syntax-check hello.yml
ansible-playbook --check hello.yml
ansible-playbook hello.yml
cat /tmp/hello.txt  # Verify output
rm -f /tmp/hello.txt  # Cleanup
```

## Development Environment

The project uses a containerized development environment:
- **Container**: Microsoft's TypeScript/Node.js base (Node 22)
- **Pre-installed tools**: Ansible, ansible-lint, yamllint, Claude Code CLI
- **Setup**: Open in VS Code with Remote-Containers extension

All development dependencies are automatically installed in the container - no manual setup required.

## Architecture

**Core Components:**
- `hello.yml`: Main Ansible playbook that displays messages and writes to `/tmp/hello.txt`
- `.github/workflows/ansible-checks.yml`: Comprehensive CI pipeline with 5-stage validation
- `.devcontainer/`: Complete development environment configuration

**Design Pattern:**
- Localhost-targeted Ansible execution
- Variable-driven configuration (`greeting_name` with default "World")
- Idempotent operations using Ansible modules (`debug`, `shell`)

## CI/CD Pipeline

The automated testing pipeline validates:
1. YAML syntax and formatting
2. Ansible best practices and rules
3. Playbook syntax validation
4. Functional execution testing
5. Output verification

Triggers on pushes to `main`/`develop` branches and pull requests to `main`.

## Branch Strategy

- **Main branch**: `main`
- **Development branches**: Supported pattern includes `develop`
- **Current working branch**: `ansible-hello`
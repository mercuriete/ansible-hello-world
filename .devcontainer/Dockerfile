FROM mcr.microsoft.com/devcontainers/typescript-node:22

# Install tools
RUN apt-get update && apt-get install -y \
    ansible \
    ansible-lint && \
    npm install -g @anthropic-ai/claude-code && \
    rm -rf /var/lib/apt/lists/*

CMD [ "sleep", "infinity" ]

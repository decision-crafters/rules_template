# DevOps Initialization Prompt


## Install kanbn globally
```
npm install -g @tosin2013/kanbn
```

## Setup ENV
```
export OPENROUTER_API_KEY=your_api_key_here
export OPENROUTER_MODEL=google/gemma-3-4b-it:free
```

## Install kanbn using podman
```
# Pull the latest container image
podman pull quay.io/takinosh/kanbn:latest
```

#### 📁 Step-by-Step:

1. **Create a wrapper script** (e.g., in `~/.local/bin`):

```bash
mkdir -p ~/.local/bin

cat << 'EOF' > ~/.local/bin/kanbn
#!/bin/bash
podman run -it --rm \
  -v "$(pwd)":/workspace:Z \
  -w /workspace \
  -e OPENROUTER_API_KEY=$OPENROUTER_API_KEY \
  quay.io/takinosh/kanbn:latest kanbn "$@"
EOF
```

2. **Make it executable**:

```bash
chmod +x ~/.local/bin/kanbn
```

3. **Ensure `~/.local/bin` is in your `PATH`** (add this to your `~/.bashrc` or `~/.zshrc` if it’s not already):

```bash
export PATH="$HOME/.local/bin:$PATH"
```

Then reload your shell:

```bash
source ~/.bashrc  # or source ~/.zshrc
```

## Step Env 

```
kanbn init
```

## Inital tasks
```
cat >boostrap.md<<EOF

EOF
```

## Add tasks 
```
kanbn add --name "Project bootstrap" --description "$(cat boostrap.md)" --column "Backlog"
curl -OL https://raw.githubusercontent.com/decision-crafters/rules_template/refs/heads/main/prompts/devops_initialization.md
kanbn add --name "Setup rules_template template for main project  "  --description "User Goal: $(cat devops_initialization.md)" --column "Backlog"
```

```
kanbn add --name "Understand and develop main project epic" --description "User Goal: $(cat README.md)" --column "Backlog"
curl -OL https://raw.githubusercontent.com/decision-crafters/rules_template/refs/heads/main/prompts/debugging_tdd_workflow.md
kanbn add --name "Setup rules_template template for main project"  --description "User Goal: $(cat debugging_tdd_workflow.md)" --column "Backlog"
```

## logging help commands
```
kanbn h  > /tmp/kanbn_help.md
kanbn add --name "kanbn cli information" --description "$(cat /tmp/kanbn_help.md)"  --column "Backlog"


```


## Commands
```
# Ask for potential sub-tasks for the main epic
kanbn chat --message "I am ready to work on project-bootstrap. The goal for me is to get this project running on this curent system. I will give you the infomration you need to work with you."
```


## When using windsur, Cursor, github Copilot or Cline use this 
```
cat >chat-with-kanban.sh<<EOF
chat-with-kanban.sh
#!/bin/bash

IDE_NAME=cursor
MESSAGE="${IDE_NAME} please change my content"

export OPENROUTER_API_KEY=your_api_key_here
export OPENROUTER_MODEL=google/gemma-3-4b-it:free
export DEBUG=false

kanbn chat --message "$MESSAGE" | tee /tmp/${IDE_NAME}_please_read_this_file.md

EOF
```


# DevOps Initialization Prompt


## Install kanbn globally
```
npm install -g @tosin2013/kanbn
```

## Setup ENV
```
export OPENROUTER_API_KEY=your_api_key_here
```

## Install kanbn using podman
```
# Pull the latest container image
podman pull quay.io/takinosh/kanbn:latest

# Run Kanbn commands using the container
podman run -it --rm \
  -v $(pwd):/workspace:Z \
  -w /workspace \
  -e OPENROUTER_API_KEY=$OPENROUTER_API_KEY \
  quay.io/takinosh/kanbn:latest kanbn <command>
```

## Step Env 

```
kanbn init
```

## Add tasks 
```
kanbn add --name "Understand and develop main project epic" --description "User Goal: $(cat README.md)" --column "Backlog"
curl -OL https://raw.githubusercontent.com/decision-crafters/rules_template/refs/heads/main/prompts/devops_initialization.md
kanbn add --name "Setup rules_template template for main project  "  --description "User Goal: $(cat devops_initialization.md)" --column "Backlog"
```

```
kanbn add --name "Understand and develop main project epic" --description "User Goal: $(cat README.md)" --column "Backlog"
curl -OL https://raw.githubusercontent.com/decision-crafters/rules_template/refs/heads/main/prompts/debugging_tdd_workflow.md
kanbn add --name "Setup rules_template template for main project  "  --description "User Goal: $(cat debugging_tdd_workflow.md)" --column "Backlog"
```

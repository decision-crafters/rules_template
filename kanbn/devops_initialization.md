# DevOps Initialization Prompt


## Install kanbn globally
npm install -g @tosin2013/kanbn

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
export OPENROUTER_API_KEY=your_api_key_here
kanbn init
```

## Add tasks 
```
kanbn add --name "Understand and develop main project epic" --description "User Goal: $(cat README.md)" --column "Backlog"
kanbn add --name "Setup rules_template template for main project  "
```
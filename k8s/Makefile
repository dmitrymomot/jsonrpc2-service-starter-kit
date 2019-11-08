.PHONY: help up down restart info log

help: ## Show this help
	@awk 'BEGIN {FS = ":.*?## "} /^[a-zA-Z_-]+:.*?## / {printf "  \033[36m%-15s\033[0m %s\n", $$1, $$2}' $(MAKEFILE_LIST)

up: ## Deployment of the API service
	@kubectl apply \
		-f $(wordlist 2,$(words $(MAKECMDGOALS)),$(MAKECMDGOALS))/config.yml \
		-f $(wordlist 2,$(words $(MAKECMDGOALS)),$(MAKECMDGOALS))/deploy.yml \
		-f $(wordlist 2,$(words $(MAKECMDGOALS)),$(MAKECMDGOALS))/service.yml

down: ## Shut down the API service
	@kubectl delete \
		-f $(wordlist 2,$(words $(MAKECMDGOALS)),$(MAKECMDGOALS))/deploy.yml \
		-f $(wordlist 2,$(words $(MAKECMDGOALS)),$(MAKECMDGOALS))/service.yml \
		-f $(wordlist 2,$(words $(MAKECMDGOALS)),$(MAKECMDGOALS))/config.yml

restart: down up info ## Restart of the API service

info: ## Get kubernetes cluster information
	@kubectl get all

log: ## Show logs
	@kubectl logs $(wordlist 2,$(words $(MAKECMDGOALS)),$(MAKECMDGOALS)) --all-containers=true

%:
	@:

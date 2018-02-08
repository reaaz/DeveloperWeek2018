# Why you need to stop using THE staging server?
## Background
* Containers 101 Meetup in MV
* Codefresh — continuous delivery for Docker, Kubernetes, and Helm
	
## Common CI/CD Process Implementation
* Changes become more expensive as you go down the line (local vs staging vs build vs prod)
* Time to get validation from business owners is harder
* Deliverables
	* Code
	* Test results
	* DB changes
	* Known issues
* Can’t do real testing (and integration testing) until staging
* Challenges
	* Friction between different environments
* Summary
	* If you can’t do integration testing until you get to staging, your change cost goes up because the feedback loop with engineering is slower
## Containers
* Every step runs inside a container (container based CI system)
* Images are a more reliable deliverable — your deliverable isn’t a changeset, it’s an image that you can deploy
* A container should only be built once then the entire process is built around that container
	* Container is a black box (need meta data around it)
* Designed for micro service architectures
* Deliverable becomes a set of containers with full history (full image report)
## Docker Native
* Test every build
* Unit, integration, security tests on build before PR
## Prerequisites
* Application portability (docker compose or helm)
* Image management (full history of artifacts)
* Hosting flexibility (Kubernetes)
* Automation engine
## Helm
* Package manger for Kubernetes
* Why?
	* Quick app portability
	* Better testing
	* Easy dev onboarding
	* Rollbacks
	* Because `kubectl apply -f` is dumb
* Deploy CRAZY microservice architectures in seconds
* Charts - packaged K8s resources
* Chart registry - registry of consumable charts (like Docker Hub)
* Release - an instance of your chart (every single one is a new release)
* Template file vs values file for different environments
## Demo
* Xray - security testing
* Pipeline
	* Build docker image
	* Run unit tests
	* Promote to artifactory (docker push)
	* Deploy with Helm
	* Fill chart with dynamic container name
	* Build Helm package
	* On-demand namespacing
		* Namespace in Kubernetes - segment a cluster (typically by application [or production and dev])

#devweek2018

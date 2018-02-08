# Keep Docker in its Box
## What Devs Love about Docker
* Huge win for developer onboarding
* Developer sharing/collaboration
* Other bundlers suck by design and by implementation  (npm, ruby gems)
* Common environment dev_test_stage/prod
* Resource efficiency
* Empowers developers
## Docker Concepts
* Container - a live running set of processes
* Docker image - bundle of files that defines your system image
* Dockerfile: Instructions for everything that’s not in your image
	* Other files to add
	* How to run your container
	* Networking services
	* Environment variables
* Orchestration - management of multiple running Docker containers
	* Interdependencies
	* Scaling and resource allocation
	* Docker compose+Swarm, Kubernetes, Mesos, AWS ECS
* Container registry
	* Place to store your images 
## What’s in a Docker image
* Whatever you had in your container when you ran `docker build`
* System configuration
* Built by developer
* Without involvement of a sysadmin
## Configuration Management
*  Define image of server in a DSL designed for the purpose
* Can manage configurations in place
* Benefits
	* Reproducible servers
	* Avoid the black box — see why a configuration is made
	* Reusable building blocks / design new configs functionally
	* Versioning of system configuration
	* Know what you have everywhere
## Using Docker without Configuration Management
* Maintain consistency between environments
* Works on your laptop, should work on prod
* No process of translating image into requirements
* No pesky ops bottleneck
## Using Docker with Configuration Management
* Ops provides docker image  
* Dev develops, updates docker image
* Ops extracts requirements, integrates into config management
* Maintain consistency between environments
* Integrate dev and ops knowledge into configs
* Building blocks make new combinations easy to get right
* Versioning is easy
* Easy integration with ops update processes (security updates, etc.)
## Advantages of Docker in prod
* Mostly eliminate production failures due to bundling/library issues
* Production issues more likely to be reproducible in dev environments
* Easy scaling (with an existing resource pool)
* Low overhead for multiple services on the same host
## Alternative approach (Docker in dev, system images in prod)
* Docker in dev, with configuration management
* System images (AMIs, etc) in production using same configuration management (like packer)
* Simplicity in production (like Amazon ECS which requires two levels of autoscaling)
	* Performance
	* Networking
	* Security
## Disadvantages of Docker in production
* Extra layers complicate performance, networking, security
* Complex orchestration is a requirement
* Autoscaling is harder, and usually less efficient
* Ephemeral infrastructure can be hard to troubleshoot (and force much more instrumentation) [logs, autoscaling issues]
* Usually more expensive
## Side note: immutability
* Only meaningful when enforced (like read-only file systems)
* Enhances security, avoids certain bugs
* Enforcing immutability is straightforward with or without Docker
## Use cases where Docker in prod is a clear win
* Many apps sharing a massively larger infrastructure
* Bursty traffic and autoscaling ramp up is too slow (1-2 minutes)
## Conclusions
* Docker can make development more efficient
* Collaboration between dev and ops is needed for service quality
* Configuration management allows you to keep Docker in sync with non-Docker and facilitates dev+ops collaboration
* Docker in production mostly adds complexity
* One size doesn’t fit all
## Questions
* Autoscaling?
	* Terraform or CloudFormation on top
#devweek2018

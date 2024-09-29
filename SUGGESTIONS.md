# Suggestions

### Project
Although I understood the structure of your project, use of docker as an lab environment (which pretty great BTW), yet for someone less fortunate it might be challanging, and frustrating trying to understand and set it up with out proper instructions:
- Intentions are good, but people (even the smart ones) may behave in a stupind manner thus keeping all the management part of the project should provide the answers to whom ever it is to use your project/code/utility

### README

- Missing link to install.md
    - I think you misunderstood the idea of this file: you need to provide step-by-step explanations for user to use your project
- Missing link to tasks.md
    

### INSTALL SCRIPT

- Missing version/purpose/author/ in shell script
- Missing strict mode (set -o pipefail; set -o errfail)

### DOCKER

- why not use `CMD["sleep", "infinity"]` for container to run all the way ?
- why not to mount localfolder, directly to ansible container ? why to copy?
- why not use docker-compose to build you lab environment ?

### ANSIBLE

- keeping binary files in git repo is generally bad idea, because, in case bad up/download the binary can be damaged and it will be hard to understand why.
    - you should have created a role, that download all the binary files locally and then inserts them in to other role `files` folder to be used for install.
- how will you manage k3s under docker container ? 
    - it is even possible ?
    - what is the point inserting `k3s-uninstall.sh` ?


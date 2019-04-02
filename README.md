# Rails Environment w/Docker
Rails environment setup for docker with multiple repository sub-folders.  Assumes the need for using docker-compose to
stand up mulitple rails development environments and be able to clone student's work into folders. Once a repo/project is 
cloned into the student's directory you can add a dockerfile for their project.

## Setup
1. Clone the repository:
  ```
    git clone https://github.com/elusive/rails-env.git
    cd rails-env
  ```
2. Copy the "new-student" directory and rename for a student or author.
  ```
  cp new-student NEW_NAME
  ```
3. ` cd` into the new directory
4. Clone project (rails app) repository inside the directory.
5. Edit the dockerfile for the newly cloned project:
  a. update ADD statement with correct name of project root directory
  ```
    ADD ./PROJ_NAME/ ./
  ```
  b. update COPY statement with correct name of project root directory
  ```
    COPY ./PROJ_NAME/ ./
  ```
6. Make similar updates to the docker-compose.yml file in the rails-env directory to include correct folder name for 
the sub-folder of the student/team member directory you just added and are trying to run the project in.

## Notes
The point of this project is to be able to reuse the docker-compose file and to re-use a single dockerfile for each 
sub-folder within the environment.  This prevents need to add a dockerfile to the (likely) other person's repository.
I created this to be able to quickly pull a mentoring student's repo from git and make a couple small edits and then
`docker-compose up` their application w/o having to worry about what dependencies they have.  

## Execution of commands
Because of the use of docker-compose we can use the services hosts names and the `docker-compose run` command to execute
any commands we might need to, inside of the dev environment.  I.e.:
```
  docker-compose run web rake db:migrate
```

Questions or problems please enter an issue or email me: john.c.gilliland@gmail.com

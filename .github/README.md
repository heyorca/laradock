This is a fork of the <a href="https://github.com/laradock/laradock">laradock</a> repo. 

# Why?

Laradock helps developers with pre-configured docker containers. It can be included as a git submodule in the project directory:

```
my-project (directory)
    public
    stuff
    laradock (submodule)
        .env
        docker-compose.yml
        some-other-stuff
```

Problem is changes inside the git submodule (e.g. docker-compose.yml) cannot be included in the main git repo of the project; limiting the developer to make configuration changes to laradock that can be committed to the repo. 

This package allows developers to use laradock in their projects, but define the laradock docker-compose.yml and .env configurations outside the laradock folder and inside their project directory. This makes it possible to submit these configuration files to the repo, making it faster for others to setup and run projects locally.

# Usage

Submodule this repo into your project:

```
git submodule add --name laradock-my-project --force https://github.com/heyorca/laradock.git laradock-my-project
```

Run `./setup.sh` from the laradock directory.

Your project tree should look something like this:

```
- my-project
    - public
    - stuff
    - laradock-my-project (submodule)
        - .env (symlink to ../laradock-env)
        - docker-compose.yml (symlink to ../laradock-docker-compose)
        - some-other-stuff
    - laradock-env
    - laradock-docker-compose.yml
```
    
You can modify the generated laradock-env and laradock-docker-compose.yml file in your project directory based on your needs. 

Run `sudo docker-compose up` from the laradock directory and the docker environments will run based on those two files.

Visit <a href="https://github.com/laradock/laradock">laradock</a> to learn more.

## License

[MIT License](https://github.com/laradock/laradock/blob/master/LICENSE)


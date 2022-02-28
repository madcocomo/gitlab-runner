This is a example project to run a self-hosting gitlab runner.

### Precondition
The host server should have docker and docker-compose installed

### Setup
1. Clone the project to the folder you want to run the runner.

2. [Optional] Run the docker-compose in keep folder to pre-load image.

```
cd keep
docker-compose up
docker-compose stop
``` 

3. Start the runner
```
# in the project folder
docker-compose up -d
```

4. Register the runner
```
docker-compose exec runner gitlab-runner register
```
input the url, token, runner name, runner type (docker), default docker image

5. Change the runner setting
Edit the `config/config.toml`. Change the envrionment, memory, and volumes according to the config.toml file in project root.

6. Enable the runner
In the gitlab Seetings -- CI/CD -- Runners, you should see the runner is running now. Edit the runner, check the `Run untagged jobs` and save change.

### Adjust the setting for your needs
You can change the pre-load images and volumes for the project to be build.

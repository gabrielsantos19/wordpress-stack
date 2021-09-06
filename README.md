# wordpress-stack

## deploy with docker-compose
1. Define the variables in the .env file as per your needs;
2. Deploy with docker-compose:
```
docker-compose -f stack.yml up -d
```

## deploy in docker swarm
1. Define the variables in the .env file as per your needs;
2. Load the variables (Note that the variables will be loaded to your environment and will persist until the end of session. If you want to avoid this, you can launch bash again with command ```bash``` and execute ```exit``` after you're done):
```
set -o allexport; source .env; set +o allexport
```
(see https://stackoverflow.com/questions/19331497/set-environment-variables-from-file-of-key-value-pairs/30969768#30969768).

3. Deploy in docker swarm:
```
docker stack deploy -c stack.yml yourStackName
```

## files
- **.env**: file with variables used to configure and auto-install Wordpress..
- **custom.ini**: custom directives for php (see https://www.php.net/manual/en/ini.core.php).
- **install.php**: this is the install script from an original Wordpress, modified to auto-install using environment variables. The added code is within the comments ```NOT ORIGINAL WORDPRESS``` and ```NOT ORIGINAL WORDPRESS END```. The commented out code is within the comments ```ORIGINAL WORDPRESS``` and ```ORIGINAL WORDPRESS END```.
- **stack.yml**: the docker file.

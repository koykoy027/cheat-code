## how to change PHP version and install packages

- check the PHP version that are available and choose your desire
```
sudo update-alternatives --config php
```

- here, I will assume to choose `PHP7.2` and install package you want
```
sudo apt-get install php7.2-<package>
```

- restart apache2
```
sudo systemctl restart apache2
```

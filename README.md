# Docker image for ulozto-downloader with working captcha solving (16.10.2022)

## Install/Build (Synology) [tested]
Requirements: enabled ssh access
              firewall setup
              SynoCLI Network tools package installed from Syncommunity repo (screen command)
              git package installed from Syncommunity repo
              user must be able to run docker command with sudo

```
▶ git clone https://github.com/kiwiiikiwiiikiwiii/ulozto-downloader/ && cd ulozto-downloader
▶ docker build -t ulozto-downloader . --network=host --no-cache
```

## Setup (Synology) [tested]

```
▶ add function to /etc.defaults/.bashrc_profile
  function ulozto-downloader { screen -dm docker run --network=host --rm -t -v <YOUR_PATH>:/d ulozto-downloader "$1"; }
▶ source /etc.defaults/.bashrc_profile
```
### Add user to run docker command with sudo
```
▶ echo "<YOUR_USER>   ALL=(ALL) NOPASSWD: /usr/local/bin/docker" >> /etc/sudoers
```
## Usage (Synology) [tested]
```
▶ ulozto-downloader URL
```

#### Example on Synology: /volume1/<SHARED_FOLDER_NAME>
```
function ulozto-downloader { screen -dm docker run --rm -t -v /volume1/ulozto:/d ulozto-downloader "$1"; }
```


------------------------------------------------------------------------------------------------------------------------------------------


## Install/Build (Ubuntu) [not tested]

```
▶ git clone https://github.com/kiwiiikiwiiikiwiii/ulozto-downloader/ && cd ulozto-downloader
▶ docker build -t ulozto-downloader . --no-cache
```

## Setup (Ubuntu) [not tested]

```
▶ add function to ~/.bashrc:
  function ulozto-downloader { screen -dm sudo docker run --rm -t -v <YOUR_PATH>:/d ulozto-downloader "$1"; }
▶ source ~/.bashrc
```
## Usage (Ubuntu) [not tested]
```
▶ ulozto-downloader URL
```
Note: `YOUR_PATH` paramater must be an absolute path to destination folder, where the file will be downloaded to, ie. your samba share.

------------------------------------------------------------------------------------------------------------------------------------------

## Note

`YOUR_PATH` paramater must be an absolute path to destination folder, where the file will be downloaded to, ie. your shared folder.
 
remove -d from function if you don't want to detach screen
 
------------------------------------------------------------------------------------------------------------------------------------------

## Debug
```
screen -m bash -c "sudo docker run --network=host --rm -t -v <YOUR_PATH>:/d ulozto-downloader "https://uloz.to/file/fZ4JME7U/trololo-3gp"; bash"
```

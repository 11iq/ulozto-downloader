
# Dockerfile of setnicka/ulozto-downloader

Docker container of [setnicka/ulozto-downloader](https://github.com/setnicka/ulozto-downloader) project


## Install/Build

```
▶ git clone https://github.com/jansramek/ulozto-downloader.git
▶ cd ulozto-downloader
▶ docker build -t ulozto-downloader .
```

## Usage

```
▶ add function to ~/.bashrc:
  function ulozto-downloader { screen -dm docker run --rm -t -v YOUR_PATH:/d ulozto-downloader --parts 20 "$1"; }
▶ source ~/.bashrc
▶ ulozto-downloader URL
```
Note: `YOUR_PATH` paramater must be an absolute path to destination folder, where the file will be downloaded to, ie. your samba share.


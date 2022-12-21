# YouCube

[![Project license](https://img.shields.io/github/license/Commandcracker/YouCube?style=for-the-badge)](https://github.com/Commandcracker/YouCube/blob/main/LICENSE.txt)
[![Mentioned in Awesome ComputerCraft](https://img.shields.io/badge/Mentioned%20in%20Awesome-ComputerCraft-violet?style=for-the-badge&logo=Awesome%20Lists&logoColor=white)](https://github.com/tomodachi94/awesome-computercraft)

[![Spellcheck Workflow Status](https://img.shields.io/github/actions/workflow/status/Commandcracker/YouCube/spellcheck.yml?branch=main&label=Spell-check&logo=github&style=for-the-badge)](https://github.com/Commandcracker/YouCube/actions/workflows/spellcheck.yml)
[![API documentation](https://img.shields.io/github/actions/workflow/status/Commandcracker/YouCube/asyncapi-doc.yml?branch=main&label=API%20documentation&logo=github&style=for-the-badge)](https://github.com/Commandcracker/YouCube/actions/workflows/asyncapi-doc.yml)

YouCube streams media from services like YouTube to [ComputerCraft: Tweaked](https://github.com/cc-tweaked/CC-Tweaked). \
**Project Status: Proof of concept**

## Installation

### Client

[![CC: Tweaked Version: 1.100+](https://img.shields.io/badge/CC:%20tweaked-1.100+-green?style=for-the-badge&logo=GNOME%20Terminal)](https://tweaked.cc/)
![or](.README/slash.svg)
[![CC: Tweaked Version: 1.80pr1.3+](https://img.shields.io/badge/CC:%20tweaked-1.80pr1.3+-green?style=for-the-badge&logo=GNOME%20Terminal)](https://tweaked.cc/)
![+](.README/plus.svg)
[![Computronics Version: 0.1.0+](https://img.shields.io/badge/Computronics-0.1.0+-green?style=for-the-badge)](https://wiki.vexatos.com/wiki:computronics)

[![Lua Lint Workflow Status](https://img.shields.io/github/actions/workflow/status/Commandcracker/YouCube/illuaminate-lint.yml?branch=main&label=Lua%20Lint&logo=github&style=for-the-badge)](https://github.com/Commandcracker/YouCube/actions/workflows/illuaminate-lint.yml)

![preview](.README/preview-client.png)

<https://user-images.githubusercontent.com/49335821/207105983-f3887269-51d2-4ea2-b8f5-4c4af87ccad4.mp4>

The client can be installed by running the following command:

```shell
pastebin run swsmNAf7
```

or

```shell
wget run https://raw.githubusercontent.com/Commandcracker/YouCube/main/installer.lua
```

#### Starting the Client

```text
youcube
```

#### Libraries

All libraries that are used by the [client](https://github.com/Commandcracker/YouCube/blob/main/client/youcube.lua).

| Library                                                                                               |
|-------------------------------------------------------------------------------------------------------|
| [argparse](https://github.com/Commandcracker/cc-argparse)                                             |
| [numberformatter](https://github.com/Commandcracker/YouCube/blob/main/client/lib/numberformatter.lua) |
| [semver](https://github.com/kikito/semver.lua)                                                        |
| [youcubeapi](https://github.com/Commandcracker/YouCube/blob/main/client/lib/youcubeapi.lua)           |

#### UnicornPKG (Experimental)

YouCube can be installed with [unicornpkg](https://unicornpkg.madefor.cc/). \
Just run `hoof install youcube` to install it.

#### LevelOS / lStore

[![lStore Package](https://img.shields.io/github/actions/workflow/status/Commandcracker/YouCube/lstore-put.yml?branch=main&label=lStore%20Package&logo=github&style=for-the-badge)](https://github.com/Commandcracker/YouCube/actions/workflows/lstore-put.yml)

On [LevelOS](https://discord.com/invite/vBsjGqy99U) YouCube can be installed by running `lStore get YouCube <path>` or `lStore get bpBYV1aG <path>` or by Using the StoreUI.

![preview](.README/levelos.png)

#### Settings

Settings that can be set with the CC: Tweaked [settings module](https://tweaked.cc/module/settings.html#v:get)

| name                  | default | Description                                     |
|-----------------------|---------|-------------------------------------------------|
| `youcube.server`      |         | First server that should be used                |
| `youcube.keys.skip`   |   32 (d)|Key code to skip song                            |
| `youcube.keys.back`   |   30 (a)|Key code to head to previous song                |
| `youcube.buffer_size` |   32    |Maximum ammount of songs that can be gone back to|

#### Events

List of events that are [queued](https://tweaked.cc/module/os.html#v:queueEvent) by youcube

| Name                     | Arguments | Description                                     |
|--------------------------|-----------|-------------------------------------------------|
| `youcube:vid_eof`        | `data`    | Called, when Video playback has ended           |
| `youcube:audio_eof`      | `data`    | Called, when Audio playback has ended           |
| `youcube:fill_buffers`   |           | Internal event (called when buffers are filled) |
| `youcube:status`         | `data`    | Status of the serversided media download        |
| `youcube:playback_ended` |           | Called, when all playback has ended             |
| `youcube:vid_playing`    | `data`    | Called, when Video playback has started         |
| `youcube:audio_playing`  | `data`    | Called, when Audio playback has started         |
| `youcube:playing`        |           | Called, when playback has started               |

### Server

[![Python Version: 3.7+](https://img.shields.io/badge/Python-3.7+-green?style=for-the-badge&logo=Python&logoColor=white)](https://www.python.org/downloads/)
[![Python Lint Workflow Status](https://img.shields.io/github/actions/workflow/status/Commandcracker/YouCube/pylint.yml?branch=main&label=Python%20Lint&logo=github&style=for-the-badge)](https://github.com/Commandcracker/YouCube/actions/workflows/pylint.yml)

![preview](.README/preview-server.png)

YouCube has a some public servers, which you can use if you don't want to host your own server. \
The client has the public servers set by default, so you can just run the client, and you're good to go. \
Moor Information about the servers can be seen on the [doc](https://commandcracker.github.io/YouCube/).

#### Requirements

- [yt-dlp/FFmpeg](https://github.com/yt-dlp/FFmpeg-Builds) / [FFmpeg 5.1+](https://ffmpeg.org/)
- [sanjuuni](https://github.com/MCJack123/sanjuuni)
- [Python 3.7+](https://www.python.org/downloads/)
  - [aiohttp](https://pypi.org/project/aiohttp/)
  - [yt-dlp](https://pypi.org/project/yt-dlp/)

You can install the required packages with [pip](https://pip.pypa.io/en/stable/installation/) by running:

```shell
pip install -r server/requirements.txt
```

#### Starting the Server

```bash
python server/youcube.py
```

#### Environment variables

Environment variables you can use to configure the server.

| Variable          | Default    | Description                                 |
|-------------------|------------|---------------------------------------------|
| `PORT`            | `5000`     | The port where the web server should run on |
| `TRUSTED_PROXIES` |            | Trusted proxies (separated by comma`,`)     |
| `FFMPEG_PATH`     | `ffmpeg`   | Path to the FFmpeg executable               |
| `SANJUUNI_PATH`   | `sanjuuni` | Path to the Sanjuuni executable             |
| `NO_COLOR`        | `False`    | Disable colored output                      |
| `LOGLEVEL`        | `DEBUG`    | Python Log level of the main logger         |

### Docker Compose

```yml
version: "2.0"
services:
  youcube:
    image: ghcr.io/commandcracker/youcube:main
    restart: always
    hostname: youcube
    ports:
      - 5000:5000
```

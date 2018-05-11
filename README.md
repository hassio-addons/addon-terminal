# Community Hass.io Add-ons: Terminal

[![GitHub Release][releases-shield]][releases]
![Project Stage][project-stage-shield]
[![License][license-shield]](LICENSE.md)

[![GitLab CI][gitlabci-shield]][gitlabci]
![Project Maintenance][maintenance-shield]
[![GitHub Activity][commits-shield]][commits]

[![Bountysource][bountysource-shield]][bountysource]
[![Discord][discord-shield]][discord]
[![Community Forum][forum-shield]][forum]

[![Buy me a coffee][buymeacoffee-shield]][buymeacoffee]

This add-on allows you to log in to your Hass.io Home Assistant instance using
a web terminal.

## About

This add-on allows you to log in to your Hass.io Home Assistant instance using
a web terminal. Giving you to access your Home Assistant configuration file and
folder, and also includes a command-line tool to do things like restart,
update, and check your instance.

![Terminal in the Home Assistant Frontend](images/screenshot.png)

## Features

- Access your terminal right from the web!
- Add-able to your Home Assistant interface.
- Compatible if Hass.io was installed via the generic Linux installer.
- Persists custom SSH client settings & keys between add-on restarts
- Have Alpine packages installed on start. This will allow you to install your
  favorite tools, which will be available every single time you log in.
- Execute custom commands on start automatically so that you can customize the
  shell to your likings.
- [ZSH][zsh] as its default shell. Easier to use for the beginner, more advanced
  for the more experienced user. It even comes preloaded with
  ["Oh My ZSH"][ohmyzsh], with some plugins enabled as well.
- Contains a sensible set of tools right out of the box: curl, Wget, RSync, GIT,
  Nmap, Mosquitto client, MariaDB/MySQL client, Awake (“wake on lan”), Nano,
  Vim, tmux, and a bunch commonly used networking tools.

## Installation

The installation of this add-on is pretty straightforward and not different in
comparison to installing any other Hass.io add-on.

1. [Add our Hass.io add-ons repository][repository] to your Hass.io instance.
1. Install the "Terminal" add-on.
1. Start the "Terminal" add-on
1. Check the logs of the "Terminal" add-on to see if everything went well.
1. Surf to your Hass.io instance and use port `7681`
    (e.g. `http://hassio.local:7681`).

**NOTE**: Do not add this repository to Hass.io, please use:
`https://github.com/hassio-addons/repository`.

## Docker status

[![Docker Architecture][armhf-arch-shield]][armhf-dockerhub]
[![Docker Version][armhf-version-shield]][armhf-microbadger]
[![Docker Layers][armhf-layers-shield]][armhf-microbadger]
[![Docker Pulls][armhf-pulls-shield]][armhf-dockerhub]
[![Anchore Image Overview][armhf-anchore-shield]][armhf-anchore]

[![Docker Architecture][aarch64-arch-shield]][aarch64-dockerhub]
[![Docker Version][aarch64-version-shield]][aarch64-microbadger]
[![Docker Layers][aarch64-layers-shield]][aarch64-microbadger]
[![Docker Pulls][aarch64-pulls-shield]][aarch64-dockerhub]
[![Anchore Image Overview][aarch64-anchore-shield]][aarch64-anchore]

[![Docker Architecture][amd64-arch-shield]][amd64-dockerhub]
[![Docker Version][amd64-version-shield]][amd64-microbadger]
[![Docker Layers][amd64-layers-shield]][amd64-microbadger]
[![Docker Pulls][amd64-pulls-shield]][amd64-dockerhub]
[![Anchore Image Overview][amd64-anchore-shield]][amd64-anchore]

[![Docker Architecture][i386-arch-shield]][i386-dockerhub]
[![Docker Version][i386-version-shield]][i386-microbadger]
[![Docker Layers][i386-layers-shield]][i386-microbadger]
[![Docker Pulls][i386-pulls-shield]][i386-dockerhub]
[![Anchore Image Overview][i386-anchore-shield]][i386-anchore]

## Configuration

**Note**: _Remember to restart the add-on when the configuration is changed._

Example add-on configuration:

```json
{
  "log_level": "info",
  "username": "hassio",
  "password": "changeme",
  "ssl": true,
  "certfile": "fullchain.pem",
  "keyfile": "privkey.pem",
  "packages": [
    "python",
    "python-dev",
    "py-pip",
    "build-base"
  ],
  "init_commands": [
    "pip install virtualenv",
    "pip install yamllint"
  ]
}
```

**Note**: _This is just an example, don't copy and past it! Create your own!_

### Option: `log_level`

The `log_level` option controls the level of log output by the addon and can
be changed to be more or less verbose, which might be useful when you are
dealing with an unknown issue. Possible values are:

- `trace`: Show every detail, like all called internal functions.
- `debug`: Shows detailed debug information.
- `info`: Normal (usually) interesting events.
- `warning`: Exceptional occurrences that are not errors.
- `error`:  Runtime errors that do not require immediate action.
- `fatal`: Something went terribly wrong. Add-on becomes unusable.

Please note that each level automatically includes log messages from a
more severe level, e.g., `debug` also shows `info` messages. By default,
the `log_level` is set to `info`, which is the recommended setting unless
you are troubleshooting.

Using `trace` or `debug` log levels puts the terminal daemon into debug mode.

### Option: `username`

This option allows you to enable authentication on accessing the terminal.
It is only used for the authentication; you will be the `root` user after
you have authenticated. Using `root` as the username is possible, but not
recommended. Leaving it empty would disable the possibility of authentication
completely.

**Note**: _If you set an `username`, `password` becomes mandatory as well._

### Option: `password`

Sets the password to authenticate with. Leaving it empty would disable the
possibility to authenticate completely.

**Note**: _If you set a `password`, `username` becomes mandatory as well._

### Option: `ssl`

Enables/Disables SSL (HTTPS) on the web terminal. Set it `true` to enable it,
`false` otherwise.

### Option: `certfile`

The certificate file to use for SSL.

**Note**: _The file MUST be stored in `/ssl/`, which is default for Hass.io_

### Option: `keyfile`

The private key file to use for SSL.

**Note**: _The file MUST be stored in `/ssl/`, which is default for Hass.io_

### Option: `packages`

Allows you to specify additional [Alpine packages][alpine-packages] to be
installed in your shell environment (e.g., Python, Joe, Irssi).

**Note**: _Adding many packages will result in a longer start-up
time for the add-on._

### Option: `init_commands`

Customize your terminal environment even more with the `init_commands` option.
Add one or more shell commands to the list, and they will be executed every
single time this add-on starts.

## Embedding into Home Assistant

It is possible to embed the terminal directly into Home Assistant, allowing
you to access your terminal through the Home Assistant frontend.

Home Assistant provides the `panel_iframe` component, for these purposes.

Example configuration:

```yaml
panel_iframe:
  terminal:
    title: Terminal
    icon: mdi:console
    url: https://addres.to.your.hass.io:7681
```

## Known issues and limitations

The following error may occur in your add-on log:

```txt
ERR: lws_context_init_server_ssl: SSL_CTX_load_verify_locations unhappy
````

This error can be safely ignored; the add-on will function properly.

## Changelog & Releases

This repository keeps a change log using [GitHub's releases][releases]
functionality. The format of the log is based on
[Keep a Changelog][keepchangelog].

Releases are based on [Semantic Versioning][semver], and use the format
of ``MAJOR.MINOR.PATCH``. In a nutshell, the version will be incremented
based on the following:

- ``MAJOR``: Incompatible or major changes.
- ``MINOR``: Backwards-compatible new features and enhancements.
- ``PATCH``: Backwards-compatible bugfixes and package updates.

## Support

Got questions?

You have several options to get them answered:

- The Home Assistant [Community Forum][forum], we have a
  [dedicated topic][forum] on that forum regarding this add-on.
- The Home Assistant [Discord Chat Server][discord] for general Home Assistant
  discussions and questions.
- Join the [Reddit subreddit][reddit] in [/r/homeassistant][reddit]

You could also [open an issue here][issue] GitHub.

## Contributing

This is an active open-source project. We are always open to people who want to
use the code or contribute to it.

We have set up a separate document containing our
[contribution guidelines](CONTRIBUTING.md).

Thank you for being involved! :heart_eyes:

## Authors & contributors

The original setup of this repository is by [Franck Nijhof][frenck].

For a full list of all authors and contributors,
check [the contributor's page][contributors].

## We have got some Hass.io add-ons for you

Want some more functionality to your Hass.io Home Assistant instance?

We have created multiple add-ons for Hass.io. For a full list, check out
our [GitHub Repository][repository].

## License

MIT License

Copyright (c) 2017 Franck Nijhof

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[aarch64-anchore-shield]: https://anchore.io/service/badges/image/1c80333f792fa5d73255a92850a12cdd838e817d1a6a048aafd606d10968c5d3
[aarch64-anchore]: https://anchore.io/image/dockerhub/hassioaddons%2Fterminal-aarch64%3Alatest
[aarch64-arch-shield]: https://img.shields.io/badge/architecture-aarch64-blue.svg
[aarch64-dockerhub]: https://hub.docker.com/r/hassioaddons/terminal-aarch64
[aarch64-layers-shield]: https://images.microbadger.com/badges/image/hassioaddons/terminal-aarch64.svg
[aarch64-microbadger]: https://microbadger.com/images/hassioaddons/terminal-aarch64
[aarch64-pulls-shield]: https://img.shields.io/docker/pulls/hassioaddons/terminal-aarch64.svg
[aarch64-version-shield]: https://images.microbadger.com/badges/version/hassioaddons/terminal-aarch64.svg
[alpine-packages]: https://pkgs.alpinelinux.org/packages
[amd64-anchore-shield]: https://anchore.io/service/badges/image/54fa4ccc2cedf45c399b4571774bfad4a1c5fed480fa46fd85d74cbc5189b2c2
[amd64-anchore]: https://anchore.io/image/dockerhub/hassioaddons%2Fterminal-amd64%3Alatest
[amd64-arch-shield]: https://img.shields.io/badge/architecture-amd64-blue.svg
[amd64-dockerhub]: https://hub.docker.com/r/hassioaddons/terminal-amd64
[amd64-layers-shield]: https://images.microbadger.com/badges/image/hassioaddons/terminal-amd64.svg
[amd64-microbadger]: https://microbadger.com/images/hassioaddons/terminal-amd64
[amd64-pulls-shield]: https://img.shields.io/docker/pulls/hassioaddons/terminal-amd64.svg
[amd64-version-shield]: https://images.microbadger.com/badges/version/hassioaddons/terminal-amd64.svg
[armhf-anchore-shield]: https://anchore.io/service/badges/image/86ab3e0caac39352e463ba9f03f08ad3224cc38216723c151e6b37c33a0bd729
[armhf-anchore]: https://anchore.io/image/dockerhub/hassioaddons%2Fterminal-armhf%3Alatest
[armhf-arch-shield]: https://img.shields.io/badge/architecture-armhf-blue.svg
[armhf-dockerhub]: https://hub.docker.com/r/hassioaddons/terminal-armhf
[armhf-layers-shield]: https://images.microbadger.com/badges/image/hassioaddons/terminal-armhf.svg
[armhf-microbadger]: https://microbadger.com/images/hassioaddons/terminal-armhf
[armhf-pulls-shield]: https://img.shields.io/docker/pulls/hassioaddons/terminal-armhf.svg
[armhf-version-shield]: https://images.microbadger.com/badges/version/hassioaddons/terminal-armhf.svg
[bountysource-shield]: https://img.shields.io/bountysource/team/hassio-addons/activity.svg
[bountysource]: https://www.bountysource.com/teams/hassio-addons/issues
[buymeacoffee-shield]: https://www.buymeacoffee.com/assets/img/guidelines/download-assets-sm-2.svg
[buymeacoffee]: https://www.buymeacoffee.com/frenck
[commits-shield]: https://img.shields.io/github/commit-activity/y/hassio-addons/addon-terminal.svg
[commits]: https://github.com/hassio-addons/addon-terminal/commits/master
[contributors]: https://github.com/hassio-addons/addon-terminal/graphs/contributors
[discord-shield]: https://img.shields.io/discord/330944238910963714.svg
[discord]: https://discord.gg/c5DvZ4e
[forum-shield]: https://img.shields.io/badge/community-forum-brightgreen.svg
[forum]: https://community.home-assistant.io/t/community-hass-io-add-on-terminal/33814?u=frenck
[frenck]: https://github.com/frenck
[gitlabci-shield]: https://gitlab.com/hassio-addons/addon-terminal/badges/master/pipeline.svg
[gitlabci]: https://gitlab.com/hassio-addons/addon-terminal/pipelines
[home-assistant]: https://home-assistant.io
[i386-anchore-shield]: https://anchore.io/service/badges/image/4219552d881e054e656091dbe78aefb4ba001bf78742543bca8df01d3b037085
[i386-anchore]: https://anchore.io/image/dockerhub/hassioaddons%2Fterminal-i386%3Alatest
[i386-arch-shield]: https://img.shields.io/badge/architecture-i386-blue.svg
[i386-dockerhub]: https://hub.docker.com/r/hassioaddons/terminal-i386
[i386-layers-shield]: https://images.microbadger.com/badges/image/hassioaddons/terminal-i386.svg
[i386-microbadger]: https://microbadger.com/images/hassioaddons/terminal-i386
[i386-pulls-shield]: https://img.shields.io/docker/pulls/hassioaddons/terminal-i386.svg
[i386-version-shield]: https://images.microbadger.com/badges/version/hassioaddons/terminal-i386.svg
[issue]: https://github.com/hassio-addons/addon-terminal/issues
[keepchangelog]: http://keepachangelog.com/en/1.0.0/
[license-shield]: https://img.shields.io/github/license/hassio-addons/addon-terminal.svg
[maintenance-shield]: https://img.shields.io/maintenance/yes/2018.svg
[ohmyzsh]: http://ohmyz.sh/
[project-stage-shield]: https://img.shields.io/badge/project%20stage-production%20ready-brightgreen.svg
[reddit]: https://reddit.com/r/homeassistant
[releases-shield]: https://img.shields.io/github/release/hassio-addons/addon-terminal.svg
[releases]: https://github.com/hassio-addons/addon-terminal/releases
[repository]: https://github.com/hassio-addons/repository
[semver]: http://semver.org/spec/v2.0.0.htm
[zsh]: https://en.wikipedia.org/wiki/Z_shell
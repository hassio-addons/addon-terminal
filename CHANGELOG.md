# Community Hass.io Add-ons: Terminal

All notable changes to this add-on will be documented in this file.

The format is based on [Keep a Changelog][keep-a-changelog]
and this project adheres to [Semantic Versioning][semantic-versioning].

## Unreleased

No unreleased changes yet.

## [v2.2.1] (2018-01-19)

[Full Changelog][v2.2.0-v2.2.1]

### Changed

- Upgrades add-on base image to v1.3.2

## [v2.2.0] (2018-01-09)

[Full Changelog][v2.1.1-v2.2.0]

### Added

- Added the new Hassio CLI v1.0.1

### Changed

- Updates forum link in other places
- Adds Supervisor>=v0.81.0 as an requirement
- Reduces clone depth of Oh My Zsh
- Upgrades add-on base image to v1.3.1
- Updated maintenance year, it is 2018

## [v2.1.1] (2017-12-27)

[Full Changelog][v2.1.0-v2.1.1]

### Fixed

- Fixed typo in CHANGELOG

### Changed

- Upgrades add-on base image to v1.3.0
- Use image tagged as test as a cache resource
- Pass local CircleCI Docker socket into the build container
- Prevents possible future Docker login issue
- Updated forum topic URL in README

### Removed

- Removes Microbadger notification hooks

## [v2.1.0] (2017-12-02)

[Full Changelog][v2.0.2-v2.1.0]

### Changed

- Upgrades add-on base image to v1.2.0
- Improves ttyd S6 run script
- Moves copy of rootfs at a later stage

### Removed

- Removes `repository.json` to prevent user to install wrong repo
- Removes Gratipay from README, since it is EOL

## [v2.0.2] (2017-10-30)

[Full Changelog][v2.0.1-v2.0.2]

### Changed

- Updated base images to v1.0.1
- Protocol adaptive 'WebUI' button #16

## [v2.0.1] (2017-10-20)

[Full Changelog][v2.0.0-v2.0.1]

### Fixed

- Terminal does not start, with SSL enabled #13 (@cogneato)

### Changed

- Updated ttyd log level to be more usefull

## [v2.0.0] (2017-10-20)

[Full Changelog][v1.0.0-v2.0.0]

### Added

- Added CodeClimate
- Added CircleCI
- Added support for Hass.io's extended label schema
- Added persistency of the ~/.ssh folder

### Changed

- Migrated to the new Hass.io build system
- Migrated to our new base images
- Rewrite of add-on onto the S6 process supervisor
- Upgraded the hassio CLI tool to the latest version
- Updated documentation

## [v1.0.0] (2017-08-16)

### Added

- First version of the Terminal Add-on
- This CHANGELOG file

[keep-a-changelog]: http://keepachangelog.com/en/1.0.0/
[semantic-versioning]: http://semver.org/spec/v2.0.0.html
[v1.0.0-v2.0.0]: https://github.com/hassio-addons/addon-terminal/compare/v1.0.0...v2.0.0
[v1.0.0]: https://github.com/hassio-addons/addon-terminal/tree/v1.0.0
[v2.0.0-v2.0.1]: https://github.com/hassio-addons/addon-terminal/compare/v2.0.0...v2.0.1
[v2.0.0]: https://github.com/hassio-addons/addon-terminal/tree/v2.0.0
[v2.0.1-v2.0.2]: https://github.com/hassio-addons/addon-terminal/compare/v2.0.1...v2.0.2
[v2.0.1]: https://github.com/hassio-addons/addon-terminal/tree/v2.0.1
[v2.0.2-v2.1.0]: https://github.com/hassio-addons/addon-terminal/compare/v2.0.2...v2.1.0
[v2.0.2]: https://github.com/hassio-addons/addon-terminal/tree/v2.0.2
[v2.1.0-v2.1.1]: https://github.com/hassio-addons/addon-terminal/compare/v2.1.0...v2.1.1
[v2.1.0]: https://github.com/hassio-addons/addon-terminal/tree/v2.1.0
[v2.1.1-v2.2.0]: https://github.com/hassio-addons/addon-terminal/compare/v2.1.1...v2.2.0
[v2.1.1]: https://github.com/hassio-addons/addon-terminal/tree/v2.1.1
[v2.2.0-v2.2.1]: https://github.com/hassio-addons/addon-terminal/compare/v2.2.0...v2.2.1
[v2.2.0]: https://github.com/hassio-addons/addon-terminal/tree/v2.2.0
[v2.2.1]: https://github.com/hassio-addons/addon-terminal/tree/v2.2.1

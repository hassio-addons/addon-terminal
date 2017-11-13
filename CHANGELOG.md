# Community Hass.io Add-ons: Terminal

All notable changes to this add-on will be documented in this file.

The format is based on [Keep a Changelog][keep-a-changelog]
and this project adheres to [Semantic Versioning][semantic-versioning].

## Unreleased

### Removed

- Removes `repository.json` to prevent user to install wrong repo

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
[v2.0.2]: https://github.com/hassio-addons/addon-terminal/tree/v2.0.2

# Community Hass.io Add-ons: Terminal

All notable changes to this add-on will be documented in this file.

The format is based on [Keep a Changelog][keep-a-changelog]
and this project adheres to [Semantic Versioning][semantic-versioning].

## Unreleased

No are unreleased changes yet.

## [v2.0.1][v2.0.1] (2017-10-20)

[Full Changelog][v2.0.0-v2.0.1]

### Fixed

- Terminal does not start, with SSL enabled [#13][13] ([cogneato][])

### Changed

- Updated ttyd log level to be more usefull

## [v2.0.0][v2.0.0] (2017-10-20)

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

## [v1.0.0][v1.0.0] (2017-08-16)

### Added

- First version of the Terminal Add-on
- This CHANGELOG file

[13]: https://github.com/hassio-addons/addon-terminal/issues/13
[cogneato]: https://github.com/cogneato
[keep-a-changelog]: http://keepachangelog.com/en/1.0.0/
[semantic-versioning]: http://semver.org/spec/v2.0.0.html
[v1.0.0-v2.0.0]: https://github.com/hassio-addons/addon-terminal/compare/v1.0.0...v2.0.0
[v1.0.0]: https://github.com/hassio-addons/addon-terminal/tree/v1.0.0
[v2.0.0-v2.0.1]: https://github.com/hassio-addons/addon-terminal/compare/v2.0.0...v2.0.1
[v2.0.0]: https://github.com/hassio-addons/addon-terminal/tree/v2.0.0
[v2.0.1]: https://github.com/hassio-addons/addon-terminal/tree/v2.0.1

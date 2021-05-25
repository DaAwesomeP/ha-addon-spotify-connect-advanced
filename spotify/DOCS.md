# DaAwesomeP Home Assistant Add-on: Spotify Connect Advanced

This is a fork of [hassio-addons/addon-spotify-connect](https://github.com/hassio-addons/addon-spotify-connect). It adds a few more features, like all of the LibreSpot options and events in Home Assistant.

The Home Assistant Spotify Connect add-on allows you to use your device,
running Home Assistant, to play your Spotify music. This add-on uses the
Spotify Connect protocol, which makes it a device that can be controlled
by all the official clients.

For example; Running Home Assistant on a Raspberry Pi with this add-on
installed will allow you to play your Spotify music on the Pi. So all you'll
have to do is hook up your sound system to the Pi and start booming!

## Installation

The installation of this add-on is pretty straightforward and not different in
comparison to installing any other Home Assistant add-on.

1. Search for the "Spotify Connect" add-on in the Supervisor add-on store
   and install it.
1. Select your audio output device and hit `Save` on that as well.
1. Start the "Spotify Connect" add-on.
1. Check the logs of the "Spotify Connect" to see if everything went well.
1. Ready to go!

## Configuration

**Note**: _Remember to restart the add-on when the configuration is changed._

Example add-on configuration:

```yaml
log_level: info
name: HomeAssistant
bitrate: 320
username: frenck@example.com
password: MySpotifyPassword
```

**Note**: _This is just an example, don't copy and paste it! Create your own!_

### Option: `log_level`

The `log_level` option controls the level of log output by the addon and can
be changed to be more or less verbose, which might be useful when you are
dealing with an unknown issue. Possible values are:

- `trace`: Show every detail, like all called internal functions.
- `debug`: Shows detailed debug information.
- `info`: Normal (usually) interesting events.
- `warning`: Exceptional occurrences that are not errors.
- `error`: Runtime errors that do not require immediate action.
- `fatal`: Something went terribly wrong. Add-on becomes unusable.

Please note that each level automatically includes log messages from a
more severe level, e.g., `debug` also shows `info` messages. By default,
the `log_level` is set to `info`, which is the recommended setting unless
you are troubleshooting.

Setting the `log_level` to `debug` will also turn on debug mode on the
Spotify service.

### Option: `name`

The name of your device (the Spotify Connect target), as shown on
the official Spotify clients.

### Option: `bitrate`

The bitrate Spotify should use. The higher, the better the sound quality,
however, the add-on consumes more data.

Valid values: `96`, `160` or `320` (default).

### Option: `username`

**IMPORTANT**: _This requires a Spotify Premium account!_

The username you use to login to your Spotify Premium account. Setting
this will bind the add-on to your account exclusively.

This can be helpful when experiencing discovery issues on your network or
to disallow guests on your network to use the add-on.

### Option: `password`

The password you use to login to your Spotify Premium account.

### Option: `additional_cli_options`

Additional CLI options. See the [LibreSpot documentation](https://github.com/librespot-org/librespot/wiki/Options). Options should include the starting two dashes (`--`) and be separated by spaces. For example:

```
--enable-volume-normalisation --volume-ctrl fixed
```

Note that adjusting settings related to PulseAudio/ALSA or other sound device settings may cause issues. Also note that the addon already makes use of the following options, and adjusting them may causes issues:

 - `bitrate`
 - `name`
 - `username` (if configured)
 - `password` (if configured)
 - `disable-audio-cache`
 - `verbose` (if in debug mode)

## Known issues and limitations

- This add-on requires a Spotify Premium account.

## Changelog & Releases

This repository keeps a change log using [GitHub's releases][releases]
functionality.

Releases are based on [Semantic Versioning][semver], and use the format
of `MAJOR.MINOR.PATCH`. In a nutshell, the version will be incremented
based on the following:

- `MAJOR`: Incompatible or major changes.
- `MINOR`: Backwards-compatible new features and enhancements.
- `PATCH`: Backwards-compatible bugfixes and package updates.

## Support

This is an unofficial addon. Please [open an issue here][issue] on GitHub.

## Authors & contributors

This is Perry Naseck (DaAwesomeP)'s fork of the [community addon](https://github.com/hassio-addons/addon-spotify-connect).

For a full list of all authors and contributors,
check [the contributor's page][contributors].

## License

MIT License

Copyright (c) 2021-present Perry Naseck

Copyright (c) 2018-2021 Franck Nijhof (from fork)

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

[contributors]: https://github.com/DaAwesomeP/ha-addon-spotify-connect-advanced/graphs/contributors
[frenck]: https://github.com/frenck
[issue]: https://github.com/DaAwesomeP/ha-addon-spotify-connect-advanced/issues
[releases]: https://github.com/DaAwesomeP/ha-addon-spotify-connect-advanced/releases
[semver]: http://semver.org/spec/v2.0.0.htm

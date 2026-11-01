# streammon

Records streams with [streamlink](https://streamlink.github.io) as a systemd user service.

## Install

```sh
./install
```

The recorder looks for `streamlink` on `PATH` and then in `~/.local/bin`. A
different path can be set in `~/.config/streammon/defaults.env`.

## Add a channel

Create `~/.config/streammon/channels/<channel>.env`:

```sh
cd ~/.config/streammon/channels
cp channel.env.example mychannel.env
$EDITOR mychannel.env   # set STREAM_URL and OUTPUT_DIR (or RECORDINGS_ROOT in defaults.env)
```

Optional: copy `channel.conf.example` to `<channel>.conf` for per-channel streamlink options.

## Manage

```sh
systemctl --user enable --now 'streammon@mychannel.service'
systemctl --user status 'streammon@mychannel.service'
journalctl --user -u 'streammon@mychannel.service' -f
```

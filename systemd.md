## Journalctl tips & tricks

### Only view last N entries (faster than piping into tail)

`journalctl -n N`

### Disk Usage

`journalctl --disk-usage`

### List Boots

`journalctl --list-boots`

### View logs since a specific date

``journalctl --since yesterday``

`journalctl --since "2022-10-15 14:40:00"`

## Temporarily inhibit sleep on closing lid
`systemd-inhibit --what=handle-lid-switch sleep 10m`

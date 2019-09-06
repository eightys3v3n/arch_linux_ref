# To switch Home/PageUp and End/PageDown on my MSI laptop.
## Get event codes for all the relevant keys.
```
sudo pacman -S evemu
sudo evemu-describe
// for my laptop it was event4 "AT Translated Set 2 Keyboard"
4
```
### Event Codes:
- KEY_HOME     = 102
- KEY_END      = 107
- KEY_PAGEUP   = 104
- KEY_PAGEDOWN = 109

## Get the scan codes for the relevant keys.
`sudo showkey --scancodes` then press the keys.
### Scan Codes:
- PGUP   = e049
- PGDOWN = e051
- HOME   = e047
- END    = e04f

## Actually rebind keys for this session
```
setkeycodes e049 102
setkeycodes e051 107
setkeycodes e047 104
setkeycodes e04f 109
```

## Make persistent
Create
```/etc/systemd/system/swap_laptop_keys.service
[Unit]
Description=Swaps the Page up/home and Page down/end keys on my laptop keyboard.
Before=multi-user.target

[Service]
Type=simple
Environment=DISPLAY=:0
ExecStart=/usr/bin/swap_laptop_keys.sh

[Install]
WantedBy=multi-user.target
```
Enable service


## Links
- wiki.archlinux.org/index.php/Map_scancodes_to_keycodes

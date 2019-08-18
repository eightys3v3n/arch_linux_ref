Put in `/etc/X11/xorg.conf.d/00-keyboard.conf`.

```
Section "InputClass"
    Identifier "default-keyboard" # Some random name.
    MatchIsKeyboard "on"
    Option "XkbLayout" "us,us" # Need the same number of layouts as variants.
    Option "XkbModel" "pc105"
    Option "XkbVariant" ",dvorak" # The first one is blank, qwerty is default.
   Option "XkbOptions" "grp:alt_shift_toggle" # Use Alt-Shift to switch.
EndSection
```

# Rose-Pine login theme for SDDM based on SDDM Sugar Dark

This is a customized version of the [Sugar Dark Theme](https://github.com/MarianArlt/sddm-sugar-dark) with colors from the [Rose Pine](https://rosepinetheme.com) palette.

This fork of [lwndhrst/sddm-rose-pine](https://github.com/lwndhrst/sddm-rose-pine) targets **Qt6** SDDM (e.g. Debian, whose SDDM is Qt6-only):

- `metadata.desktop` sets `QtVersion=6`; without it SDDM looks for the Qt5 `sddm-greeter` binary and silently falls back to the default theme.
- `QtGraphicalEffects` no longer exists in Qt6, so the components import `Qt5Compat.GraphicalEffects` instead.
- Qt6 passes empty `theme.conf` values (`FontSize=`, `HeaderText=`) to QML as `undefined` rather than `""`, so those checks test truthiness instead of `!== ""`.
- Qt6's per-state palettes give the disabled user-icon button an opaque black background and let the hidden user `ComboBox` draw the first letter of the username next to the icon; both get an empty `Item` instead. The default placeholder text colour is also unreadable on the dark fields, so it is set explicitly.

`background.jpg` is the maintainer's wallpaper rather than upstream's. To use a different one, put it in the theme directory and set `Background=` in a `theme.conf.user` there rather than editing `theme.conf`.

### Dependencies

[`sddm >= 0.21.0`](https://github.com/sddm/sddm) built against Qt6, Qt Quick Controls 2, Qt SVG and the Qt5Compat graphical effects (Debian: `qml6-module-qt5compat-graphicaleffects`).

### Installing the theme

Clone this repository into the theme directory of SDDM:

```
$ sudo git clone https://github.com/hcfx86/sddm-rose-pine-qt6.git /usr/share/sddm/themes/sddm-rose-pine
```
This will put all files in a folder called "sddm-rose-pine" inside of the themes directory of SDDM.  

After that you will have to point SDDM to the new theme by editing its config file, preferrably at `/etc/sddm.conf.d/sddm.conf` *(create if necessary)*. You can take the default config file of SDDM as a reference: `/etc/sddm.conf/usr/lib/sddm/sddm.conf.d/sddm.conf`.  

In the `[Theme]` section simply add the themes name: `Current=sddm-rose-pine`. Also see the [Arch wiki on SDDM](https://wiki.archlinux.org/index.php/SDDM).

### Theming the theme

Sugar is extremely customizable by editing its included `theme.conf` file. You can change the colors and images used, the time and date formats, the appearance of the whole interface and even how it works.  
And as if that wouldn't still be enough you can translate every single button and label because SDDM is still lacking behind with localization and clearly [needs your help](https://github.com/sddm/sddm/wiki/Localization)!

Please read the [Sugar Wiki on Github](https://github.com/MarianArlt/sddm-sugar-light/wiki/Before-you-begin) for a detailed description of every variable available, what it does and the values it accepts. The `theme.conf` itself is also very well commented for you to get right at it.

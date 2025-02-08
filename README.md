# Linux Desktop Shortcuts

This repository is a practical guide to creating `.desktop` shortcuts on Linux, allowing you to add applications to the application menu even when installed manually.

## Creating a `.desktop` shortcut

If you have a binary of an application installed manually and want to create it in the Linux application menu, follow the steps below:

### 1 Create the `.desktop` file
Open a terminal and run:

```sh
nano ~/.local/share/applications/APP-NAME.desktop
```

### 2 Add the following content and adjust as needed:

```ini
[Desktop Entry]
Version=1.0
Type=Application
Name=Application name
Exec=/path/for/your/binary
Icon=/path/for/your/icone.png
Categories=Development;Utilities;
Terminal=false
StartupWMClass=WMClassName
```

**Field explanation:**
- `Exec`: Absolute path to the application binary.
- `Icon`: Path to the application icon.
- `Categories`: Sets the application category in the menu.
- `Terminal`: If `true`, the program opens in the terminal; if `false`, it opens normally.
- `StartupWMClass`: Used to identify the application window correctly.

### 3 Make the file executable

```sh
chmod +x ~/.local/share/applications/APP-NAME.desktop
```

### 4 Update the application database

```sh
gtk-update-icon-cache
update-desktop-database ~/.local/share/applications/
```

### 5 Update and check if it appears in the menu

If the shortcut doesn't appear immediately, try running:

```sh
xdg-desktop-menu forceupdate
```

If it still doesn't appear, please restart your session.

## Practical example: Creating a shortcut for Android Studio

If Android Studio is installed in `~/Documents/android-studio/`, the `.desktop` file would look like this:

```ini
[Desktop Entry]
Version=1.0
Type=Application
Name=Android Studio
Exec=/home/usuario/Documentos/android-studio/bin/studio.sh
Icon=/home/usuario/Documentos/android-studio/bin/studio.png
Categories=Development;IDE;
Terminal=false
StartupWMClass=jetbrains-studio
```

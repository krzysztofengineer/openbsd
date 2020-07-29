# Font

## Download the font

Create fonts directory inside `.local/share`:

```
mkdir -p ~/.local/share/fonts
cd ~/.local/share/fonts
```

Download the font (e.g. Fira Code):

```
git clone https://github.com/tonsky/FiraCode
```

Update fonts cache:

```
fc-cache
```

You can list available fonts with:

```
fc-list
```

## Apply font

For dwm, edit `config.def.h`:

```
static const char *fonts[] = { "Fira Code Medium:size=14" };
static const char dmenufont[] =  "Fira Code Medium:size=14" };
```

Change the font name and size for your needs.

Remove `config.h` and re-compile:

```
doas rm config.h
doas make clean install
```

Restart dwm to apply changes with `Shift + Mod + Q`

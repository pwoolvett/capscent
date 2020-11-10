# capscent - Spanish accents with capslock with xmodmap

Capslock is useless, and I need to write in spanish.

Enter capscent, a script to enable accented letters and `ñ` using the caps lock key, via `xmodmap`.

## prerequisites

* xmodmap
* If you don't already have a `.Xmodmap` file, create one:

  ```shell
  $ xmodmap -pke > ~/.Xmodmap
  ```
* Make sure you're sourcing it somewhere. For example, in `~/.xinitrc`:

  ```shell
  usermodmap=$HOME/.Xmodmap
  if [ -f "$usermodmap" ]; then
    xmodmap "$usermodmap"
  fi
  ```

## Install

This will be a script. For now, 

1. Add this to the beginning of your `~/.Xmodmap`:
   ```
   clear lock
   clear control
   add control = Caps_Lock Control_L Control_R
   keycode  26 = e E eacute Eacute
   keycode  30 = u U uacute Uacute
   keycode  31 = i I iacute Iacute
   keycode  32 = o O oacute Oacute
   keycode  38 = a A aacute Aacute
   keycode  48 = apostrophe quotedbl dead_acute quotedbl
   keycode  66 = Mode_switch Caps_Lock Caps_Lock Caps_Lock Caps_Lock Caps_Lock
   ```
   
   (adjust accordingly for keycodes depending on your lang/kb)

1. Comment (add a `!` at the beginning of each line) for each of the keycodes in previous step

## Usage

* `capslock` is now the "accent" trigger: hold `capslock` then press and release a vowel (or `n`): it will type it accented. For example, `capslock+a` types `á`.
* The `quote` also received a special treatment. Now `capslock+'` "types" `dead_acute`. Ok it doesn't actually type anything, but the next key will have the accent. For example, `capslock+'` then `a` types `á`.
* The default capslock feature can be accessed with `shift+capslock`.

NOTE: for capital letters, order matters: `shift+caps+a` sends a normal `a`, and then enables caps lock. Instead, to insert `Á`, type `capslock+shift+a`.

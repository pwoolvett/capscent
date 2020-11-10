# capscent - Spanish accents with capslock with xmodmap

Capslock is useless, and I need to write in spanish.

Enter capscent, a script to 

## prerequisites

* xmodmap
* If you don't already have a `.Xmodmap` file, create one:

  ```shell
  $ xmodmap -pke > ~/.Xmodmap
  ```
* Make sure you're sourcing it somewhere. For example, in `~/.xinitrc`:

  ```shell
  $HOME/.Xmodmap
  if [ -f "$usermodmap" ]; then
    xmodmap "$usermodmap"
  fi
  ```

## Install




## Usage

* `capslock` is now the "accent" trigger: hold `capslock` then press and release a vowel (or `n`): it will type it accented. For example, `capslock+a` types `á`.
* The `quote` also received a special treatment. Now `capslock+'` "types" `dead_acute`. Ok it doesn't actually type anything, but the next key will have the accent. For example, `capslock+'` then `a` types `á`.
* The default capslock feature can be accessed with `shift+capslock`.

NOTE: for capital letters, order matters: `shift+caps+a` sends a normal `a`, and then enables caps lock. Instead, to insert `Á`, type `capslock+shift+a`.

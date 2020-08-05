# XSwitcher - keyboard layout switcher for linux

This is a fork of part of another repository (https://github.com/ds-voix/VX-PBX/tree/master/x%20switcher).

Additional info here: [here](https://habr.com/ru/post/495748/) (Russian text) or [here](draft.txt) (English text)

Unlike the original, the cyclical change of the layout along the left Control key is disabled here.

## Compile and install

You must have a golang compiler (https://golang.org/doc/install).
Then install the required dependencies.

``` bash
sudo apt-get install libx11-dev libxmu-dev
go get "github.com/micmonay/keybd_event"
go get "github.com/gvalkov/golang-evdev"
go get "github.com/BurntSushi/toml"
go get "github.com/spf13/pflag"
```

Then build xswitcher.

```bash
go build -o bin/xswitcher -ldflags "-s -w" --tags static_all src/*.go
```

Xswitcher needs a root permissions to work. Copy xswitcher from bin to user's home directory and then change file mode and owner.

```bash
chmod +xs xswitcher
sudo chown root:root xswitcher
```

Now you can add xswitcher to your DE autostart.
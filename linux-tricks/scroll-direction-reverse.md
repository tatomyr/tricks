# How to Set Reverse Mouse Scrolling Direction

To set reverse mouse wheel scrolling direction on Ubuntu 16.04 (perhaps on other systems as well) like on MacOS you need to:

  * list your input devices with:

  ```
  $ xinput
  ```

  and find in there your physical pointer device (something like 'RAPOO RAPOO 5G Wireless Device' or 'Logitech USB Receiver' etc) id. Note, that it can be several identical devices. In that case, you should use each id further

  * justify the device properties with:

  ```
  $ xinput --list-props <id>
  ```

  If everything is correct it should appear a bunch of properties which contains among other:

  ```
  ...
  Evdev Scrolling Distance:	1, 1, 1
  ...
  ```

  * re set appropriate property with:

  ```
  $ xinput set-prop <id> "Evdev Scrolling Distance" -1 1 1
  ```

  Changes will be valid until system restart

  * sake of automatization you can add the task in 'Startup Applications' and it will run each time your PC starts. Sometimes there are few records refer to your physical device. Since you should set props for all of them, you have to add an appropriate amount of startup programs consequently, not chaining line.

### Lubuntu notes

As Lubuntu uses `libinput`, we have to enable the natural scrolling in such way. Open
```
sudo -H nano /usr/share/X11/xorg.conf.d/40-libinput.conf
```
and add `Option "NaturalScrolling" "true"` in an appropriate section(s).

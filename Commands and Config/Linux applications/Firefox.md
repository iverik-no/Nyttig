# Firefox

## Block Snap package

First, uninstall Firefox Snap:

`sudo snap remove firefox`

`cd ~/snap`

`rm -r firefox`


Make config files that block the snap package. Dunno which one is better, [option one](https://www.debugpoint.com/remove-firefox-snap-ubuntu/) or [option two](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04). I used both.
Paste the whole block as one; not as separate lines.

```
echo '
Package: firefox*
Pin: release o=Ubuntu*
Pin-Priority: -1
' | sudo tee /etc/apt/preferences.d/firefox-no-snap
```

```
echo '
Package: *
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 1001
' | sudo tee /etc/apt/preferences.d/mozilla-firefox
```

Now add the Mozillateam PPA:

`sudo add-apt-repository ppa:mozillateam/ppa`

Install Firefox:

`sudo apt update`

`sudo apt install firefox`


## KDE file picker

In about:config, search for

`widget.use-xdg-desktop-portal.file-picker`

Change value from 2 (default) to 1.

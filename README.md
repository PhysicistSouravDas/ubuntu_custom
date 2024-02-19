# Ubuntu Customizations

Here, I will store all ubuntu customizations done by me, from various sources.

**Table of Contents**

* [Battery Health Charging](#battery-health-charging)
* [Nodejs and npm](#nodejs-npm)
* [Environment Variables PATH](#env-vars-path)
* [Dock](#dock)

## Battery Health Charging {#battery-health-charging} [🔗](#battery-health-charging)

If laptop is regularly plugged in to electricity, then, maintaining a charge at about 60% to 80% prolongs the battery life.

So, I will customize this behaviour in Ubuntu 20.04.3 LTS.

Put this in `/etc/crontab`:
```bash
@reboot root echo 60 > /sys/class/power_supply/BAT0/charge_control_end_threshold
```
This most probably only works in ASUS Laptops.

Source: 

* [https://askubuntu.com/a/1264105](https://askubuntu.com/a/1264105)
* [https://www.osbusters.net/2021/01/enable-asus-battery-health-charging-in-linux-os.html](https://www.osbusters.net/2021/01/enable-asus-battery-health-charging-in-linux-os.html)

## Nodejs and npm {#nodejs-npm} [🔗](#nodejs-npm)

On Ubuntu, I install nodejs and npm this way:
```bash
sudo apt install nodejs npm
```
After this, there is an npm package which can manage and update nodejs. 
```bash
sudo npm update -g
```
To uninstall and remove, do this:
```bash
sudo apt --auto-remove purge nodejs
sudo apt --auto-remove purge npm
```
And also check using `which node` and `which npm`. If any file present in `usr/bin/` or `usr/bin/local`. Most likely `npm` file is present.

The below is the most recommended way
```bash
sudo npm install -g n
sudo n lts
```
Source: 

* [https://stackoverflow.com/a/41196107](https://stackoverflow.com/a/41196107)

## Environment Variables PATH {#env-vars-path} [🔗](#env-vars-path)

Suppose I have downloaded a galaxy fitting software *galfit*, which is in the folder `~/Downloads/galfit3-debian64/galfit`. *galfit* is an executable, and it is terminal based. Then, to run it, I would have to type `~/Downloads/galfit3-debain64/galfit` everytime from the $HOME folder. There is a way by which we just have to type `galfit` from anywhere in the terminal to execute it. To do so, we have to add the PATH of the software's location.

I have created a directory `.env_vars/bin`, where I will store the executables. Some PATHs are already added, via which we can run `python3` from any folder. We have to add the PATH in `~/.bashrc` text file. Add the following line to the end of `~/.bashrc`.
```bash
export PATH="$PATH:/$HOME/.env_vars/bin"
```
The preceding `$PATH:` is to add all the existing PATHs, otherwise they will be overwritten, and no other command, such as `ls`, `sudo`, `python3` will work. We just have to append the new PATH to the existing PATHs. To check the currently added PATHs, use to following command in the terminal:
```bash
echo $PATH"
```
The output will be like this:
```bash
/home/physicistsouravdas/gems/bin:/home/physicistsouravdas/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin://home/physicistsouravdas/.env_vars/bin
```

## Dock {#dock} [🔗](#dock)

The dock in Ubuntu can be fully customized. If you don't want the default sticky dock at the left, then one can use GNOME Shell Extensions, which has many options to customize the dock.

To move the *Show Applications* icon to the top/front, then, 
```bash
gsettings set org.gnome.shell.extensions.dash-to-dock show-apps-at-top true
```
Many other options can be explored. If you want to get the value of a setting, just use `get` instead of `set`.

Source:

* [https://askubuntu.com/a/966777](https://askubuntu.com/a/966777)

---

Last Updated: 20th February 2024

###### Note: To run markdown server, run `python3 -m ReadEm.serve`
**Thanks to [ReadEm](https://github.com/jockerz/ReadEm) for the Markdown server.**

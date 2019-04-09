# prettygrub
Grub theme - template for horizontal-grub menu

==============================================

[StylishDark/Vimix](https://github.com/vinceliuice/grub2-themes) grub theme was used as a base, but is heavily modified.

**Special thanks** to @sgse (aka [sgs](https://forum.manjaro.org/u/sgs/summary) at Manjaro Forum), for his valuable contribution with images, wallpaper and extensive testing. Without good company, coding or any work is boring!

==============================================

<img src="https://raw.githubusercontent.com/petsam/prettygrub/master/screenshot-1024x768.png"/>

==============================================


This grub(2) theme was created with focus on multi-booting systems and combined with [horizontal-grub](https://github.com/petsam/horizontal-grub) script, although it may be used with a normal grub menu, with optional modifications.
### Theme Installation
Install it like a grub theme as usual:

* Download the prettygrub package (it's a grub theme folder). Rename the folder to prettygrub (or any other name you like...).
* Copy the folder to `/boot/grub/themes`
* Edit `/etc/default/grub` and set the theme value to the new theme. For example:
 ```
GRUB_THEME="/boot/grub/themes/prettygrub/theme.txt"
```
### Grub menu modification
To make your grub menu look like a fake horizontal (you will better understand when you see it in action):

* Download the latest [horizontal-grub](https://github.com/petsam/horizontal-grub).
* Make the script executable, run it
* When you are asked to save to system, answer one of:
   -  No
      * Copy the created `horizontal-grub.cfg` to a folder in $HOME (an example command is given in the terminal output)
      * Review the file and/or test it with [grub2-theme-preview](https://github.com/hartwork/grub2-theme-preview) to decide if you like it
  - Yes
     * The new grub.cfg will be copied to `/boot/grub/grub.cfg`, backing up your current file.

### Installation (short version):
```
git clone https://github.com/petsam/prettygrub.git
rm -rf prettygrub/.git
sudo cp -R prettygrub /boot/grub/themes/
sudo sed -i '/GRUB_THEME\=/ c GRUB_THEME\=\"\/boot\/grub\/themes\/prettygrub\/theme.txt\"' /etc/default/grub
sudo update-grub
git clone https://github.com/petsam/horizontal-grub.git
./horizontal-grub/horizontal-grub
# answer Yes to save as system file
```

### Previewing the theme
If you want to preview how the new theme looks like you may:
* Install (if not already) `grub2-theme-preview` from AUR
* Preview the theme with (check `--help` for other options):
```
sudo grub2-theme-preview /boot/grub/themes/prettygrub
```

### Theming details
#### Icons
The distro icons in the `icons` folder, need to be transformed (when adding/changing to a custom icon).
Resize canvas (height = width x 2), setting the new (transparent) space at the top.
For example, using Pinta:
* Resize canvas.
* Extend direction to up.
* Don't keep proportions.
* Set height to double of width.

#### Theme settings
In `theme.txt`
* The distro large icon at the top is created by a second menu (top-menu)
```
+ boot_menu {
  left = 5%
  top = 10%
  width = 2
  height = 35%
  item_font = "Lato 12"
  item_color = "#000000"
  selected_item_color = "#000000"
  item_height = 12
  item_spacing = 0
  item_padding = 0
  icon_height = 280
  icon_width = 140
}
```
In order to hide the menu entries, it has to be
```
item_color = selected_item_color = desktop-color
```
When you use a wallpaper image (Global property `desktop-image`), it has to have a monochrome color at the top left quarter.

There are two countdown options for demonstration. One is enough. You may remove one of the two (or not).

Everything else is as with common grub themes. Further modifications depend on the artistic view of the theme devs.
# Gladrags - an applet to smarten up your MATE panels

This applet allows you to apply effects to the backgrounds of your panels, so that the desktop wallpaper behind them appears e.g. blurred or pixellated. In other words, gratuitous eye-candy... 

Examples:

**Without Gladrags - a normal panel with black background and 50% transparency**
![Without Gladrags](https://github.com/robint99/screenshots/raw/master/gladrags%20not%20running.png)

**Gladrags and greyscale effect:**
![greyscale](https://github.com/robint99/screenshots/raw/master/gladrags%20greyscale.png)

**Gladrags with a medium blur effect:**
![medium blur](https://github.com/robint99/screenshots/raw/master/gladrags%20medium%20blur.png)

**Gladrags with a medium pixellation effect:**
![medium pixellation](https://github.com/robint99/screenshots/raw/master/gladrags%20medium%20pixellation.png)

**Gladrags with a medium smear effect:**
![medium smear](https://github.com/robint99/screenshots/raw/master/gladrags%20medium%20smear.png)

Via the preferences dialog it is possible to specify the amount of the effect to apply and whether to apply the effect to all panels or just the panel containing the applet.
 
![Gladrags preferences](https://github.com/robint99/screenshots/raw/master/gladrags%20prefs.png)

Gladrags will also automatically update panel backgrounds whenever your desktop wallpaper changes.

Note: because Gladrags overrides the usual panel background settings, you now need to specify the panel background colour and transparency level from the applet preferences. Also, if you use the MATE dock applet, make sure that it isn't set to change the panel background colour according the wallpaper image - this will cause Gladrags and the dock applet to both try to alter the panel background settings at the same time. At best you may end up with an ugly panel, at worst one or both applets may crash.  

## How it works

Gladrags uses the wonderful [ImageMagick](http://www.imagemagick.org/script/index.php "ImageMagick Homepage") for cropping images and applying effects. The process is as follows:

    * Gladrags calculates what parts of the background image are behind the panel(s)
    * ImageMagick is then used to:
        * Crop the parts of the background image which are behind the panel(s)
        * Apply the required effect at the required level to the cropped images
        * Apply the specified background colour at the specified transparency level to the cropped images
    * Gladrags then sets the panels to use the these images as their background
     
## Limitations

Currently there is no support for multi-monitor setups, but this is planned for the future. Gladrags may or may not work correctly in this situation - it is currently untested.
Also, for Gladrags to work, you must change your wallpaper settings so that the style is set to either 'Zoom' or 'Stretch'.
Gladrags only works with background images. It won't work if e.g. you have a colour gradient set as your background.

## Installation

Installation is currently only from source. Dependencies are:

* Python3
* ImageMagick
* Python 3 Cairo bindings

You'll also need autotools and libglib2 to compile the preferences schema (e.g on Ubuntu this is libglib2.0-dev)

then cd to the directory containing all of the development files and run:

```
aclocal

automake --add-missing

autoreconf
```

To build a GTK2 version of the applet:
```
./configure --prefix=/usr
```

To build a GTK3 version:
```
./configure --prefix=/usr --with-gtk3
```

Then enter the following commands:
```
make

sudo make install
```

Acknowledgements:

Thanks to the [Variety wallpaper changer](http://peterlevi.com/variety/ "Variety") for giving me the idea of using ImageMagick to apply effects to panels backgrounds, and for being an awesome program!
 
[ImageMagick](http://www.imagemagick.org/script/index.php "ImageMacick Homepage") (obviously...)
 
Finally, the Gladrags icon is by [Freepik](http://www.freepik.com "Freepik") from [Flaticon](http://www.flaticon.com "Flaticon") and is licensed under [Creative Commons V3.0](http://creativecommons.org/licenses/by/3.0/ "Creative Commons BY 3.0") 

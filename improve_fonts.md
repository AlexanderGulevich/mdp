# Improve Fonts
## Newest
Make your Arch fonts beautiful easily!
This is what I do when I install Arch Linux to improve the fonts.

You may consider the following settings to improve your fonts for system-wide usage without installing a patched font library packages (eg. Infinality):

Install some fonts, for example:  
```sudo pacman -S ttf-dejavu ttf-liberation noto-fonts```  

Enable font presets by creating symbolic links:  
```sudo ln -s /etc/fonts/conf.avail/70-no-bitmaps.conf /etc/fonts/conf.d```  
```sudo ln -s /etc/fonts/conf.avail/10-sub-pixel-rgb.conf /etc/fonts/conf.d```  
```sudo ln -s /etc/fonts/conf.avail/11-lcdfilter-default.conf /etc/fonts/conf.d```

The above will disable embedded bitmap for all fonts, enable sub-pixel RGB rendering, and enable the LCD filter which is designed to reduce colour fringing when subpixel rendering is used.

Enable FreeType subpixel hinting mode by editing:

```/etc/profile.d/freetype2.sh```

Uncomment the desired mode at the end:

```  export FREETYPE_PROPERTIES="truetype:interpreter-version=40"```

For font consistency, all applications should be set to use the serif, sans-serif, and monospace aliases, which are mapped to particular fonts by fontconfig.

Create /etc/fonts/local.conf with following:
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
   <match>
      <edit mode="prepend" name="family">
         <string>Noto Sans</string>
      </edit>
   </match>
   <match target="pattern">
      <test qual="any" name="family">
         <string>serif</string>
      </test>
      <edit name="family" mode="assign" binding="same">
         <string>Noto Serif</string>
      </edit>
   </match>
   <match target="pattern">
      <test qual="any" name="family">
         <string>sans-serif</string>
      </test>
      <edit name="family" mode="assign" binding="same">
         <string>Noto Sans</string>
      </edit>
   </match>
   <match target="pattern">
      <test qual="any" name="family">
         <string>monospace</string>
      </test>
      <edit name="family" mode="assign" binding="same">
         <string>Noto Mono</string>
      </edit>
   </match>
</fontconfig>
```  
Set your font settings to match above in your DE system settings.

## Infinality Remix

If you want to use infinality you should try [https://github.com/pdeljanov/infinality-remix](https://github.com/pdeljanov/infinality-remix)  
**TL;DR**  
```yay -S freetype2-infinality-remix fontconfig-infinality-remix cairo-infinality-remix```

Enable font presets by creating symbolic links:  
```sudo ln -s /etc/fonts/conf.avail/70-no-bitmaps.conf /etc/fonts/conf.d```  
```sudo ln -s /etc/fonts/conf.avail/10-sub-pixel-rgb.conf /etc/fonts/conf.d```  
```sudo ln -s /etc/fonts/conf.avail/11-lcdfilter-default.conf /etc/fonts/conf.d```  

To be sure, inside /etc/fonts/local.conf add with following  
change *Favourite* for your selected font (i.e Source Sans Pro, Droid Sans, Droid Serif, etc):  
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit mode="assign" name="hinting">
      <bool>true</bool>
    </edit>
    <edit mode="assign" name="autohint">
      <bool>false</bool>
    </edit>
    <edit mode="assign" name="hintstyle">
      <const>hintslight</const>
    </edit>
    <edit mode="assign" name="rgba">
      <const>rgb</const>
    </edit>
    <edit mode="assign" name="lcdfilter">
      <const>lcddefault</const>
    </edit>
    <edit mode="assign" name="antialias">
      <bool>true</bool>
    </edit>
  </match>
   <match>
      <edit mode="prepend" name="family">
         <string>Favourite Sans</string>
      </edit>
   </match>
   <match target="pattern">
      <test qual="any" name="family">
         <string>serif</string>
      </test>
      <edit name="family" mode="assign" binding="same">
         <string>Favourite Serif</string>
      </edit>
   </match>
   <match target="pattern">
      <test qual="any" name="family">
         <string>sans-serif</string>
      </test>
      <edit name="family" mode="assign" binding="same">
         <string>Favourite Sans</string>
      </edit>
   </match>
   <match target="pattern">
      <test qual="any" name="family">
         <string>monospace</string>
      </test>
      <edit name="family" mode="assign" binding="same">
         <string>Favourite Mono</string>
      </edit>
   </match>  
</fontconfig>
```  
The following fonts are recommended and should be installed for a good experience:

 * Caladea (`ttf-caladea`)
 * Carlito (`ttf-carlito`)
 * DejaVu (`ttf-dejavu`)
 * Impallari Cantora (`aur/ttf-impallari-cantora`)
 * Liberation (`ttf-liberation`)
 * Noto (`noto-fonts`)
 * Open Sans (`ttf-opensans`)
 * Overpass (`otf-overpass`)
 * Roboto (`ttf-roboto`)
 * TeX Gyre (`tex-gyre-fonts`)
 * Ubuntu (`ttf-ubuntu-font-family`)
 * Courier Prime (`aur/ttf-courier-prime`)
 * Gelasio (`aur/ttf-gelasio-ib`)
 * Merriweather (`aur/ttf-merriweather`)
 * Source Sans Pro (`aur/ttf-source-sans-pro-ibx`)
 * Signika (`aur/ttf-signika`)

## Older and deprecated

To improve the fonts in Arch we first need to add some additional fonts. Add the following to the terminal:

```sudo pacman -S ttf-bitstream-vera ttf-inconsolata ttf-ubuntu-font-family ttf-dejavu ttf-freefont ttf-linux-libertine ttf-liberation```  

```yay -S ttf-ms-fonts ttf-vista-fonts ttf-monaco ttf-qurancomplex-fonts```

Next we will disable bitmat fonts, which are used as a fallback. 

```sudo ln -s /etc/fonts/conf.avail/70-no-bitmaps.conf /etc/fonts/conf.d```

Now we need to add the Infinality repo to our pacman.conf file. To do this, open the file with gedit (or whatever text editor your using):

```sudo vim /etc/pacman.conf```

Add the following to your pacman.conf to use the infinality repo:
```
[infinality-bundle]
SigLevel = Never
Server = http://bohoomil.com/repo/$arch

[infinality-bundle-multilib]
SigLevel = Never
Server = http://bohoomil.com/repo/multilib/$arch

[infinality-bundle-fonts]
SigLevel = Never
Server = http://bohoomil.com/repo/fonts
```
Then uncomment the multilib on pacman configuration to download and install 32 bit package on 64 bit systems
```
[multilib] 
Include = /etc/pacman.d/mirrorlist
```
Install the bundle:

```sudo pacman -Syy infinality-bundle infinality-bundle-multilib # all question answer yes```

Finally, reboot your system.
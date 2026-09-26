### Wallpaper 



### STEPS FOR THEME & WALLPAPER SWITCHER (For HYPRLOCK)
1. Have a global colors file, two accent colors get imported here
2. Use a source = /path/to/colors/file/colors.json
3. Have a script that dynamically changes the full global color file based on selected theme
4. Have a global file with wallpaper path in it
5. Have a script that changes wallpaper path & switches wallpaper using awww wallpaper daemon bash cmd
6. Import the wallpaper file here using source = /path/to/desired/wallpaper
e.g.
```
source = ~/.config/themes/gruvbox-material.conf
$accent_colour_1 = $fg # <- this guy should work after creating colors.conf file

// For some reason this wasn't working for time, date & text but worked for Input-Field's border color (literally no clue why, try to debug)
```


### step 1


- Example Structure
- 
```bash

hyprbubu/
file structure tree

╭(love)-[~/hyprbuti]  main
╰─> ls
config  mainstaller  packages  README.md  scripts
.
├── config
│   ├── bash
│   ├── hypr
│   │   ├── Fonts
│   │   │   ├── SF Pro Display
│   │   │   │   ├── SF Pro Display Bold.otf
│   │   │   │   └── SF Pro Display Regular.otf
│   │   │   └── steelfish outline regular
│   │   │       └── steelfish.outline-regular.otf
│   │   ├── helpmenu
│   │   │   └── hyprhelpmenu.txt
│   │   ├── hypridle.conf
│   │   ├── hyprland.conf
│   │   ├── hyprlock.conf
│   │   ├── hyprlockphotos
│   │   │   ├── foregroundimage
│   │   │   │   ├── buduti.png
│   │   │   │   └── butilove.png
│   │   │   ├── hyprlockForeImages.rasi
│   │   │   ├── hyprlockWallpapers-bg.rasi
│   │   │   └── lockbackground
│   │   │       ├── Dark_Nature.png
│   │   │       ├── dearsunset.jpg
│   │   │       ├── hypr.png
│   │   │       └── lovebubu.png
│   │   ├── hyprpaper.conf
│   │   ├── hyprsubconfig
│   │   │   ├── animations_alt.conf
│   │   │   ├── applicationStyle.conf
│   │   │   ├── colors.conf
│   │   │   ├── decorations.conf
│   │   │   ├── env_variables.conf
│   │   │   ├── exec.conf
│   │   │   ├── gestures.conf
│   │   │   ├── globalvaribles.conf
│   │   │   ├── input.conf
│   │   │   ├── keybinds.conf
│   │   │   ├── layout.conf
│   │   │   ├── misc.conf
│   │   │   ├── monitors.conf
│   │   │   ├── note.txt
│   │   │   ├── permissions.conf
│   │   │   └── windowRules.conf
│   │   └── scripts
│   │       ├── applauncher
│   │       │   └── appmenu.sh
│   │       ├── bluetooth.sh
│   │       ├── hyprlock
│   │       │   ├── hyprlockforeImage.sh
│   │       │   └── hyprlockWallpaper_bg.sh
│   │       ├── hyprmenu
│   │       │   └── hyprhelpmenu.sh
│   │       ├── powermenu
│   │       │   └── rofipowermenu.sh
│   │       ├── wallpaper
│   │       │   ├── wallpaper-restore.sh
│   │       │   └── wallpaperSwitch.sh
│   │       └── waybar
│   │           ├── brightness.sh
│   │           ├── lock.sh
│   │           ├── netspeed.sh
│   │           ├── power.sh
│   │           ├── waybar-css-themes-switch.sh
│   │           └── waybar-pair-switch.sh
│   ├── kitty
│   │   ├── kitty.conf
│   │   └── kitty-themes
│   │       ├── 00-Default.conf
│   │       ├── 01-Wallust.conf
│   │       ├── 3024_Day.conf
│   │       ├── 3024_Night.conf
│   │       ├── AdventureTime.conf
│   │       ├── Afterglow.conf
│   │       ├── AlienBlood.conf
│   │       ├── Alucard.conf
│   │       ├── Apprentice.conf
│   │       ├── Argonaut.conf
│   │       ├── Arthur.conf
│   │       ├── AtelierSulphurpool.conf
│   │       ├── Atom.conf
│   │       ├── AtomOneLight.conf
│   │       ├── ayu.conf
│   │       ├── ayu_light.conf
│   │       ├── ayu_mirage.conf
│   │       ├── Batman.conf
│   │       ├── Belafonte_Day.conf
│   │       ├── Belafonte_Night.conf
│   │       ├── BirdsOfParadise.conf
│   │       ├── Blazer.conf
│   │       ├── Borland.conf
│   │       ├── Bright_Lights.conf
│   │       ├── Broadcast.conf
│   │       ├── Brogrammer.conf
│   │       ├── C64.conf
│   │       ├── Chalkboard.conf
│   │       ├── Chalk.conf
│   │       ├── Ciapre.conf
│   │       ├── CLRS.conf
│   │       ├── Cobalt2.conf
│   │       ├── Cobalt_Neon.conf
│   │       ├── CrayonPonyFish.conf
│   │       ├── Dark_Pastel.conf
│   │       ├── Darkside.conf
│   │       ├── Desert.conf
│   │       ├── DimmedMonokai.conf
│   │       ├── DotGov.conf
│   │       ├── Dracula.conf
│   │       ├── Dumbledore.conf
│   │       ├── Duotone_Dark.conf
│   │       ├── Earthsong.conf
│   │       ├── Elemental.conf
│   │       ├── ENCOM.conf
│   │       ├── Espresso.conf
│   │       ├── Espresso_Libre.conf
│   │       ├── Fideloper.conf
│   │       ├── FishTank.conf
│   │       ├── Flat.conf
│   │       ├── Flatland.conf
│   │       ├── Floraverse.conf
│   │       ├── FrontEndDelight.conf
│   │       ├── FunForrest.conf
│   │       ├── Galaxy.conf
│   │       ├── Github.conf
│   │       ├── Glacier.conf
│   │       ├── GoaBase.conf
│   │       ├── Grape.conf
│   │       ├── Grass.conf
│   │       ├── gruvbox_dark.conf
│   │       ├── gruvbox_light.conf
│   │       ├── Hardcore.conf
│   │       ├── Harper.conf
│   │       ├── Highway.conf
│   │       ├── Hipster_Green.conf
│   │       ├── Homebrew.conf
│   │       ├── Hurtado.conf
│   │       ├── Hybrid.conf
│   │       ├── IC_Green_PPL.conf
│   │       ├── IC_Orange_PPL.conf
│   │       ├── idleToes.conf
│   │       ├── IR_Black.conf
│   │       ├── Jackie_Brown.conf
│   │       ├── Japanesque.conf
│   │       ├── Jellybeans.conf
│   │       ├── JetBrains_Darcula.conf
│   │       ├── Kibble.conf
│   │       ├── Later_This_Evening.conf
│   │       ├── Lavandula.conf
│   │       ├── LiquidCarbon.conf
│   │       ├── LiquidCarbonTransparent.conf
│   │       ├── LiquidCarbonTransparentInverse.conf
│   │       ├── Man_Page.conf
│   │       ├── Material.conf
│   │       ├── MaterialDark.conf
│   │       ├── Mathias.conf
│   │       ├── Medallion.conf
│   │       ├── Misterioso.conf
│   │       ├── Molokai.conf
│   │       ├── MonaLisa.conf
│   │       ├── Monokai_Classic.conf
│   │       ├── Monokai.conf
│   │       ├── Monokai_Pro.conf
│   │       ├── Monokai_Pro_(Filter_Machine).conf
│   │       ├── Monokai_Pro_(Filter_Octagon).conf
│   │       ├── Monokai_Pro_(Filter_Ristretto).conf
│   │       ├── Monokai_Pro_(Filter_Spectrum).conf
│   │       ├── Monokai_Soda.conf
│   │       ├── N0tch2k.conf
│   │       ├── Neopolitan.conf
│   │       ├── Neutron.conf
│   │       ├── NightLion_v1.conf
│   │       ├── NightLion_v2.conf
│   │       ├── Nova.conf
│   │       ├── Novel.conf
│   │       ├── Obsidian.conf
│   │       ├── Ocean.conf
│   │       ├── OceanicMaterial.conf
│   │       ├── Ollie.conf
│   │       ├── OneDark.conf
│   │       ├── Parasio_Dark.conf
│   │       ├── PaulMillr.conf
│   │       ├── PencilDark.conf
│   │       ├── PencilLight.conf
│   │       ├── Piatto_Light.conf
│   │       ├── Pnevma.conf
│   │       ├── Pro.conf
│   │       ├── Red_Alert.conf
│   │       ├── Red_Sands.conf
│   │       ├── Relaxed_Afterglow.conf
│   │       ├── Renault_Style.conf
│   │       ├── Renault_Style_Light.conf
│   │       ├── Rippedcasts.conf
│   │       ├── Royal.conf
│   │       ├── Seafoam_Pastel.conf
│   │       ├── SeaShells.conf
│   │       ├── Seti.conf
│   │       ├── Shaman.conf
│   │       ├── Slate.conf
│   │       ├── Smyck.conf
│   │       ├── snazzy.conf
│   │       ├── SoftServer.conf
│   │       ├── Solarized_Darcula.conf
│   │       ├── Solarized_Dark.conf
│   │       ├── Solarized_Dark_Higher_Contrast.conf
│   │       ├── Solarized_Dark_-_Patched.conf
│   │       ├── Solarized_Light.conf
│   │       ├── Source_Code_X.conf
│   │       ├── Spacedust.conf
│   │       ├── SpaceGray.conf
│   │       ├── SpaceGray_Eighties.conf
│   │       ├── SpaceGray_Eighties_Dull.conf
│   │       ├── Spiderman.conf
│   │       ├── Spring.conf
│   │       ├── Square.conf
│   │       ├── Sundried.conf
│   │       ├── Symfonic.conf
│   │       ├── Tango_Dark.conf
│   │       ├── Tango_Light.conf
│   │       ├── Teerb.conf
│   │       ├── Thayer_Bright.conf
│   │       ├── The_Hulk.conf
│   │       ├── Tokyo_Night.conf
│   │       ├── Tomorrow.conf
│   │       ├── Tomorrow_Night_Blue.conf
│   │       ├── Tomorrow_Night_Bright.conf
│   │       ├── Tomorrow_Night.conf
│   │       ├── Tomorrow_Night_Eighties.conf
│   │       ├── ToyChest.conf
│   │       ├── Treehouse.conf
│   │       ├── Twilight.conf
│   │       ├── Ubuntu.conf
│   │       ├── Urple.conf
│   │       ├── Vaughn.conf
│   │       ├── VibrantInk.conf
│   │       ├── WarmNeon.conf
│   │       ├── Wez.conf
│   │       ├── WildCherry.conf
│   │       ├── Wombat.conf
│   │       ├── Wryan.conf
│   │       └── Zenburn.conf
│   ├── rofi
│   │   ├── applauncher
│   │   │   └── applauncher.rasi
│   │   ├── colors
│   │   │   ├── adapta.rasi
│   │   │   ├── arc.rasi
│   │   │   ├── black.rasi
│   │   │   ├── blak.rasi
│   │   │   ├── catppuccin.rasi
│   │   │   ├── cyberpunk.rasi
│   │   │   ├── dracula.rasi
│   │   │   ├── everforest.rasi
│   │   │   ├── gruvbox.rasi
│   │   │   ├── lovelace.rasi
│   │   │   ├── navy.rasi
│   │   │   ├── nord.rasi
│   │   │   ├── onedark.rasi
│   │   │   ├── paper.rasi
│   │   │   ├── solarized.rasi
│   │   │   ├── tokyonight.rasi
│   │   │   └── yousai.rasi
│   │   ├── fonts
│   │   │   ├── fonts.rasi
│   │   │   ├── GrapeNuts-Regular.ttf
│   │   │   ├── Icomoon-Feather.ttf
│   │   │   ├── Iosevka-Nerd-Font-Complete.ttf
│   │   │   └── JetBrains-Mono-Nerd-Font-Complete.ttf
│   │   ├── powermenu
│   │   │   └── powermenu.rasi
│   │   └── wallpaper
│   │       └── wallpapers.rasi
│   ├── tmux
│   │   └── tmux.conf
│   ├── waybar
│   │   ├── base
│   │   │   └── config.jsonc
│   │   ├── config.jsonc -> /home/love/.config/waybar/base/config.jsonc
│   │   ├── style.css -> /home/love/.config/waybar/themes/cyberpunkfloat.css
│   │   ├── styles
│   │   │   ├── style_10.css
│   │   │   ├── style_11.css
│   │   │   ├── style_1.css
│   │   │   ├── style_2.css
│   │   │   ├── style_3.css
│   │   │   ├── style_4.css
│   │   │   ├── style_5.css
│   │   │   ├── style_6.css
│   │   │   ├── style_7.css
│   │   │   ├── style_8.css
│   │   │   └── style_9.css
│   │   ├── themes
│   │   │   ├── cappuccinMochaFloat.css
│   │   │   ├── cyberpunk.css
│   │   │   ├── cyberpunkfloat.css
│   │   │   ├── DraculaFloat.css
│   │   │   ├── material.css
│   │   │   ├── MaterialOceanFloat.css
│   │   │   ├── nordFloat.css
│   │   │   ├── originalsimple.css
│   │   │   ├── simplefloat.css
│   │   │   ├── solarized.css
│   │   │   └── SolarizedDarkFloat.css
│   │   ├── themespair
│   │   │   └── themes.css
│   │   └── waybarthemepair
│   │       ├── V1
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V1.png
│   │       ├── V1.0tonybar
│   │       │   ├── config.jsonc
│   │       │   └── style.css
│   │       ├── V1.2
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V1.2.png
│   │       ├── V1.3
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V13.png
│   │       ├── V1.5
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V15.png
│   │       ├── V1.6
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V16.png
│   │       ├── V2
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V2.png
│   │       ├── V2.1
│   │       │   ├── config.jsonc
│   │       │   ├── rose-pine.css
│   │       │   ├── style.css
│   │       │   └── v21.png
│   │       ├── V2.1a
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── window_pill.py
│   │       ├── V2.1b
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── window_pill.py
│   │       ├── V2.1c
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V21c.png
│   │       ├── V2.2
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V22.png
│   │       ├── V2.3
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V23.png
│   │       ├── V2.4
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V24.png
│   │       ├── V2.5
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V25.png
│   │       ├── V2.6
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V26.png
│   │       ├── V2.7
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V27.png
│   │       ├── V2.7b
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V27b.png
│   │       ├── V2.8
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V28.png
│   │       ├── V3
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V3.png
│   │       ├── V3.1
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V3shadow.png
│   │       ├── V3.2
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V3border.png
│   │       ├── V3.3
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V3border2.png
│   │       ├── V3.4
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V3trans.png
│   │       ├── V3.5
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V35.png
│   │       ├── V3.6
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V36.png
│   │       ├── V3.6a
│   │       │   ├── cava.sh
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V36a.png
│   │       ├── V3.7
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V3min3.png
│   │       ├── V4
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V4.png
│   │       ├── V4.2
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V42.png
│   │       ├── V4.3
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V43.png
│   │       ├── V4.4
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V44.png
│   │       ├── V5
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V5.png
│   │       ├── V5.b
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V5b.png
│   │       ├── V5.c
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V5c.png
│   │       ├── V5.d
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V5d.png
│   │       ├── V5.e
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V5e.png
│   │       ├── V6
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V6.png
│   │       ├── V6.a
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V6.a.png
│   │       ├── V6.aa
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V6.aa.png
│   │       ├── V6.ab
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V6.ab.png
│   │       ├── V6.ac
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V6.ac.png
│   │       ├── V6.b
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V6b.png
│   │       ├── V6.c
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V6c.png
│   │       ├── V6.ca
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V6ca.png
│   │       ├── V6.cb
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   ├── V6.cb.png
│   │       │   └── window_pill.py
│   │       ├── V6.cc
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V6.cc.png
│   │       ├── V6.cd
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V6cd.png
│   │       ├── V6.ce
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V6.ce.png
│   │       ├── V6.d
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V6d.png
│   │       ├── V6.e
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V6e.png
│   │       ├── V6.f
│   │       │   ├── config.jsonc
│   │       │   ├── style.css
│   │       │   └── V6.f.png
│   │       └── V6.fa
│   │           ├── config.jsonc
│   │           ├── style.css
│   │           └── V6fa.png
│   └── wofi
│       ├── config
│       └── style.css
├── mainstaller
├── packages
│   ├── pkgslist-pacman.txt
│   ├── pkgslist.txt
│   └── pkgslist-yay.txt
├── README.md
└── scripts
    ├── archysetup.sh
    ├── install-pacman.sh
    ├── install-yay.sh
    └── packages.sh

90 directories, 443 files




```
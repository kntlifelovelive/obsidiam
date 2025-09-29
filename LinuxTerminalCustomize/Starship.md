

```bash 
format = """
[╭─](bold blue)[░▒▓](#a3aed2)\
$directory\
[](fg:#769ff0 bg:#394260)\
$git_branch\                                                                 $git_status\
[](fg:#394260 bg:#212736)\
$nodejs\
$rust\
$golang\                                                                     $php\
[](fg:#212736 bg:#1d2230)\
$time\
[ ](fg:#1d2230)\                                                            \n$character"""

[os]
disabled = false
style = "bg:#769ff0 fg:#2e3440"


[os.symbols]
Ubuntu = "🌿"
Mint = "󰣭"
Linux = "󰌽"
Manjaro = ""

# Directory
[directory]
style = "bg:
```

```bash

6 format = """
   75 [╭─](bold blue)[░▒▓](#a3aed2)\
   74 $directory\
   73 [](fg:#769ff0 bg:#394260)\
   72 $git_branch\
   71 $git_status\
   70 [](fg:#394260 bg:#212736)\
   69 $nodejs\
   68 $rust\
   67 $golang\
   66 $php\
   65 [](fg:#212736 bg:#1d2230)\
   64 $time\
   63 [ ](fg:#1d2230)\
   62 \n$character"""
   61
   60 [os]
   59 disabled = false
   58 style = "bg:#769ff0 fg:#2e3440"
   57
   56
   55 [os.symbols]
   54 Ubuntu = "🌿"
   53 Mint = "󰣭"
   52 Linux = "󰌽"
   51 Manjaro = ""
   50
   49 # Directory
   48 [directory]
   47 style = "bg:#769ff0 fg:#2e3440"
   46 format = '($style)[   $path/ ](bg:#769ff0 fg:#2e3440)(fg:#769ff0 bg:#394260)'
   45 truncation_length = 3
   44 truncation_symbol = "…/"
   43
   42
   41 [git_branch]
   40 symbol = ""
   39 style = "bg:#394260"
   38 format = '[[ $symbol $branch ](fg:#769ff0 bg:#394260)]($style)'
   37
   36 [git_status]
   35 style = "bg:#394260"
   34 format = '[[($all_status$ahead_behind )](fg:#769ff0 bg:#394260)]($style)'
   33
   32 [nodejs]
   31 symbol = ""
   30 style = "bg:#212736"
   29 format = '[[ $symbol ($version) ](fg:#769ff0 bg:#212736)]($style)'
   28
   27 [rust]
   26 symbol = ""
   25 style = "bg:#212736"
   24 format = '[[ $symbol ($version) ](fg:#769ff0 bg:#212736)]($style)'
   23
   22 [golang]
   21 symbol = ""
   20 style = "bg:#212736"
   19 format = '[[ $symbol ($version) ](fg:#769ff0 bg:#212736)]($style)'
   18
   17 [php]
   16 symbol = ""
   15 style = "bg:#212736"
   14 format = '[[ $symbol ($version) ](fg:#769ff0 bg:#212736)]($style)'
   13
   12 [time]
    disabled = false
    time_format = "%R" # Hour:Minute Format
     style = "bg:#1d2230"
     format = '[[  $time ](fg:#a0a9cb bg:#1d2230)]($style)'
    
     # Character (Arrow at bottom line)
     [character]
     success_symbol = "[╰─>](bold blue)"
     error_symbol = "[╰─×](bold red)"
    2

```
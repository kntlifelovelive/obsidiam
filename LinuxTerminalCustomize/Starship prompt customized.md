
```

format = """  
[╭─](bold blue)[░▒▓](#a3aed2)\  
$username(bg:#a3aed2 fg:#090c0c)\  
$hostname(bg:#769ff0 fg:#a3aed2)\  
$directory\  
[](fg:#769ff0 bg:#394260)\  
$git_branch\  
$git_status\  
[](fg:#394260 bg:#212736)\  
$nodejs\  
$rust\  
$golang\  
$php\  
[](fg:#212736 bg:#1d2230)\  
$time\  
[ ](fg:#1d2230)\  
\n$character"""  
  
  
# Username  
[username]  
show_always = true  
style_user = "bg:#a3aed2 fg:#090c0c"  
style_root = "bg:#a3aed2 fg:#090c0c"  
format = '($style)[$user](bg:#a3aed2 fg:#090c0c)'  
  
# Hostname  
[hostname]  
ssh_only = false  
style = "bg:#a3aed2 fg:#2e3440"  
format = '[@$hostname](bg:#a3aed2 fg:#2e3440)'  
disabled = false  
  
  
# Directory  
[directory]  
style = "bg:#769ff0 fg:#2e3440"  
format = '($style)[  $path ](bg:#769ff0 fg:#2e3440)(fg:#769ff0 bg:#394260)'  
truncation_length = 3  
truncation_symbol = "…/"  
  
  
[git_branch]  
symbol = ""  
style = "bg:#394260"  
format = '[[ $symbol $branch ](fg:#769ff0 bg:#394260)]($style)'  
  
[git_status]  
style = "bg:#394260"  
format = '[[($all_status$ahead_behind )](fg:#769ff0 bg:#394260)]($style)'  
  
[nodejs]  
symbol = ""  
style = "bg:#212736"  
format = '[[ $symbol ($version) ](fg:#769ff0 bg:#212736)]($style)'  
  
[rust]  
symbol = ""  
style = "bg:#212736"  
format = '[[ $symbol ($version) ](fg:#769ff0 bg:#212736)]($style)'  
  
[golang]  
symbol = ""  
style = "bg:#212736"  
format = '[[ $symbol ($version) ](fg:#769ff0 bg:#212736)]($style)'  
  
[php]  
symbol = ""  
style = "bg:#212736"  
format = '[[ $symbol ($version) ](fg:#769ff0 bg:#212736)]($style)'  
  
[time]  
disabled = false  
time_format = "%R" # Hour:Minute Format  
style = "bg:#1d2230"  
format = '[[  $time ](fg:#a0a9cb bg:#1d2230)]($style)'  
  
# Character (Arrow at bottom line)  
[character]  
success_symbol = "[╰─>](bold blue)"  
error_symbol = "[╰─×](bold red)"

```


![[IMG_20250705_021115_987.jpg]]
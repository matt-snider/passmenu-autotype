# passmenu-autotype
A [dmenu](http://tools.suckless.org/dmenu/)-based interface to [pass](https://www.passwordstore.org/) that allows copying and autotyping credentials.

In comparison to [passmenu](https://git.zx2c4.com/password-store/tree/contrib/dmenu/passmenu), this script will type both the username and password.

# Usage
`passmenu-autotype` accepts the same arguments as passmenu, but additionally supports `--userfield` which should indicate the field name in the metadata section of the password file where the username can be found.

    passmenu-autotype [--type [--userfield fieldname]] [dmenu arguments...]


## Example
Given password files of the following format:
```txt
passw0rd
username: matt-snider
```

The correct command to autotype the username and password would be:

    passmenu-autotype --type --userfield username [dmenu arguments...]

This would spawn a dmenu prompt, and after selecting a file and providing the password, the autotype would be activated.


# Installation
 * Enable pass extensions: set `PASSWORD_STORE_ENABLE_EXTENSIONS=true`
 * Clone this repo and create a symlink to passmenu-autotype.bash in ~/.password-store/.extensions

Additionally, set keybindings to trigger the dmenu prompt. For example in i3:

```txt
# $mod + p: simply copies password to clipboard
bindsym $mod+p exec passmenu-autotype -q -h 20 -fn "12:normal" -w 700

# $mod + shift + p: does autotype
bindsym $mod+Shift+p exec passmenu --type --userfield username -q -h 20 -fn "12:normal" -w 700
```

  2022 Linux Rice

## General Notes
* Font: JetBrains Mono Nerd Font, Cozette??
* Visualizers: wava
* Machine: Thinkpad T14
* Colorscheme: Gruvbox
----------------------------------------------------------------
## Updating Mirrors

----------------------------------------------------------------
## Login Customization
**Set logon message**: /etc/issues is a text file that can contain text to display on screen before logging in to the tty.
----------------------------------------------------------------
## Compositor
###Different Forks
* hopefully main picom fork gets updated
* pijulius/picom (picom-pijulius-git) has the best animations by far, but not 100% configurable. Has Rouned corners but cannot do blur.
* jonaburg/picom (picom-jonaburg-git) has rounded corners, blur, but animations are not as good
### pijulius/picom
* Installed from AUR picom-pijulius-git
* Setup config file in .config/picom/picom.conf
* Start as daemon in xinitrc 
* worked off of this .conf: https://github.com/podiki/dot.me/blob/master/picom/.config/picom.conf but can also use the one from pijulius
* launch with the following in xinitrc or by wm
```
picom -b --animations --animation-window-mass 0.5 --animation-for-open-window zoom --animation-stiffness 350
```
----------------------------------------------------------------
## Fonts
### NerdFonts in Alacritty
* Install JetBrainsMono nerd font via the AUR. In Alacritty the font is referenced as "JetBrainsMono Nerd Font" (no quotes)
* Set the font for Regular, Bold, Italic, etc. in the alacritty .yml file
----------------------------------------------------------------
## Terminal
### Alacritty
* Search for the example alacritty.yml file and uncomment/rework what is needed, place at .config/alacritty/alacritty.yml
* Fonts use font families and point sizes
----------------------------------------------------------------
## Shell 
*Setting up bash, vi mode, try out ZSH and other shells later*
**Launch Program**: nerdfetch (aur)
### Bash and zsh Vi Mode
https://www.youtube.com/watch?v=hIJh-KlQ7io
Place the following at the bottom of the .bashrc:
```
set -o vi
bind -m vi-command 'Control-l: clear-screen'
bind -m vi-insert 'Control-l: clear-screen'
```
### Starship prompt
* Install starship via command from website
* Add the following to the very bottom of the .bashrc:
```
eval "$(starship init bash)"
```
----------------------------------------------------------------
## Email with Neomutt & Muttwizard
* Setup muttwizard with -f flag, add the following to the corresponding account rc:
```
set ssl_starttls = yes
set ssl_force_tls = yes
```
* Setup corresponding cron job using muttwizard
* Need to setup notifications
----------------------------------------------------------------
## Awesome Window Manager
*Managing the manager*
### Autostarting apps
**Make apps run once when awesome starts**
```
local function run_once(cmd_arr)
    for _, cmd in ipairs(cmd_arr) do
        awful.spawn.with_shell(string.format("pgrep -u $USER -fx '%s' > /dev/null || (%s)", cmd, cmd))
    end
end

run_once({ "unclutter -root" }) -- comma-separated entries
```
**XDG autostart specification**
* Prerequisite is *dex*
```
awful.spawn.with_shell(
    'if (xrdb -query | grep -q "^awesome\\.started:\\s*true$"); then exit; fi;' ..
    'xrdb -merge <<< "awesome.started:true";' ..
    -- list each of your autostart commands, followed by ; inside single quotes, followed by ..
    'dex --environment Awesome --autostart --search-paths "$HOME/.config/autostart"' -- https://github.com/jceb/dex
)
```
----------------------------------------------------------------
## Backups
*Managing backups and timeshift*
----------------------------------------------------------------
## File Manager
*GUI and TUI*
----------------------------------------------------------------
## Power Management
----------------------------------------------------------------
## NetworkManager
----------------------------------------------------------------
## Keyboard
----------------------------------------------------------------
## Mouse & Trackpoint
----------------------------------------------------------------
## Audio
----------------------------------------------------------------
## Bluetooth
*Tools, setting up applet*
----------------------------------------------------------------
## Neovim
*Setting up my custom neovim config*
----------------------------------------------------------------
## Xorg
----------------------------------------------------------------
## Bar
*Implementing awesome bar, tray icons, more*
----------------------------------------------------------------
## Screens
*Making changes stick
----------------------------------------------------------------
## Dockmode
*Handling thinkpad when docked* 
----------------------------------------------------------------
## File Syncing
*Managing SyncThing*
----------------------------------------------------------------
## Defaults
*Setting default programs*


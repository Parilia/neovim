# neovim
My personal neovim config

## Requiremtns
Latest <a href="https://neovim.io/">neovim</a> [stable]<br>
### Soft Requirements
<a href="https://github.com/vifm/vifm">vifm</a> <br>  (Other file managers can be hot swapped in, see the vifm custom terminal in the init. Also netrw is setup so you dont need this if you dont want it, just comment out or remove the vifm custom terminal in the init.)<br>
<a href="https://github.com/jesseduffield/lazygit">LazyGit</a>  <br> (If you are going to use git then I highly reccommend this.)<br>

# Back up your exsisting config
```bash
mv ~/.config/nvim ~/.config/nvim_backup
```
# Clone repo
```
git clone https://github.com/Parilia/neovim.git ~/.config/nvim
```
# nvim switcher, add to your bashrc, zshrc or POSIX Shell.
To add a new config simply rename the nvim folder in the .config, if you are cloning a new one change the name of the nvim folder in the command to what you want it to or use the above command to back up your config as getting a new one will overrite your existing one or may not even download.

```bash
# nvim switcher, you can invoke your config using the alias or by typing "nvims" into your shell
# Set an alias for your config [not needed for default nvim]
alias nvchad="NVIM_APPNAME=nvchad nvim"
alias lvim="NVIM_APPNAME=lvim nvim"

# Add config to the items
nvims() {
  items=("default" "nvchad" "lvim")
  config=$(printf "%s\n" "${items[@]}" | fzf --prompt=" Neovim Config  " --height=~50% --layout=reverse --border --exit-0)
  if [[ -z $config ]]; then
    echo "Nothing selected"
    return 0
  elif [[ $config == "default" ]]; then
    config=""
  fi
  NVIM_APPNAME=$config nvim $@
}
```

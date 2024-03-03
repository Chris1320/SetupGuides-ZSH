# Zsh

> "The [Z shell](https://www.zsh.org/) is a Unix shell that can be used as an
> interactive login shell and as a command interpreter for shell scripting.
> Zsh is an extended Bourne shell with many improvements, including some
> features of Bash, ksh, and tcsh."

\- [Wikipedia](https://en.wikipedia.org/wiki/Z_shell)

## Customization Features

This customization guide will do the following changes:

- Use **[ZSH](https://www.zsh.org/)** as your default terminal.
  (can be disabled by adding `--install-only` flag)
- Install [oh-my-zsh](https://ohmyz.sh/), a zsh framework.
- Install [powerlevel10k](https://github.com/romkatv/powerlevel10k),
  a custom theme for zsh.

This customization guide will also help you install/enable the following plugins:

| Plugin                                                                                              | Description                                                            |
| --------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| [command-not-found](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/command-not-found)       | Provide suggested packages to be installed if a command is not found.  |
| [fd](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/fd)                                     | Add completions for `fd` file searcher.                                |
| [fzf](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/fzf)                                   | Enable fuzzy auto-completion.                                          |
| [gh](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/gh)                                     | Add completions for `gh` GitHub CLI.                                   |
| [poetry](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/poetry)                             | Add completions for `poetry`, a Python dependency manager.             |
| [python](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/python)                             | Add useful aliases for `python` operations.                            |
| [qrcode](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/qrcode)                             | Generate QR codes from your terminal.                                  |
| [ripgrep](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/ripgrep)                           | Add completions for `rg` text searcher.                                |
| [ssh-agent](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/ssh-agent)                       | Automatically start `ssh-agent`.                                       |
| [sudo](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/sudo)                                 | Prefix current/previous command with `sudo` by pressing `<ESC>` twice. |
| [tmux](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/tmux)                                 | Add useful aliases for `tmux` terminal multiplexer.                    |
| [urltools](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/urltools)                         | Encode/Decode URL strings from your terminal.                          |
| [wd](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/wd)                                     | Jump or "_warp_" to directories quickly.                               |
| [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)                             | A plugin that will auto suggest commands based on your zsh history.    |
| [zsh-interactive-cd](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/zsh-interactive-cd)     | Press `<TAB>` when cd'ing to launch fzf.                               |
| [zsh-navigation-tools](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/zsh-navigation-tools) | Better navigation in zsh.                                              |
| [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)                     | A plugin that will provide syntax highlighting in your zsh shell.      |

It will also install the following packages for productivity:

| Package                                          | Description                                                   |
| ------------------------------------------------ | ------------------------------------------------------------- |
| [bat](https://github.com/sharkdp/bat)            | A modern replacement for `cat`. (aliased to `cat` by default) |
| [eza](https://github.com/eza-community/eza)      | A modern replacement for `ls`. (aliased to `ls` by default)   |
| [fd](github.com/sharkdp/fd)                      | A file searcher.                                              |
| [fzf](https://github.com/junegunn/fzf)           | A fuzzy finder.                                               |
| [git](https://git-scm.com/)                      | A version control system.                                     |
| [ripgrep](https://github.com/BurntSushi/ripgrep) | A text searcher.                                              |
| [tealdeer](https://github.com/dbrgn/tealdeer)    | Simplified, example-based, and community-driven man pages.    |
| [tmux](https://github.com/tmux/tmux/)            | A terminal multiplexer.                                       |
| [zoxide](https://github.com/ajeetdsouza/zoxide)  | A smarter `cd` command. (aliased to `cd` by default)          |

## Installation

The installation script has been tested on the following platforms:

- Kali Linux WSL
- Linux Mint 21
- Termux Android Terminal Emulator

### Automatic Installation & Customization

Download and run the install script using either of the following commands:

- Using _wget_: `$ bash <(wget -q -O - "https://raw.githubusercontent.com/SetupGuides/ZSH/main/install") install`
- Using _curl_: `$ bash <(curl -sSf "https://raw.githubusercontent.com/SetupGuides/ZSH/main/install") install`

To disable changing the default shell and opening ZSH, run with `--install-only` flag. Example:

`$ bash <(curl -sSf "https://raw.githubusercontent.com/SetupGuides/ZSH/main/install") install --install-only`

### Manual Installation & Customization

> [***NOTE***] Manual customization instructions are currently outdated.

> [***NOTE***] This guide assumes that you are using `apt` as your package manager.

1. Update apt and install zsh, wget, and git if not yet installed. `$ sudo apt update && sudo apt install --upgrade zsh wget git`
2. Change the shell to zsh. `$ chsh -s $(which zsh)`[^1]
3. Reload your terminal.
4. Download Oh-My-Zsh. `$ sh -c "$(wget -q -O - https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`
5. Install powerlevel10k. `$ git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH}/custom/themes/powerlevel10k`
6. Install zsh-autosuggestions. `$ git clone --depth=1 https://github.com/zsh-users/zsh-autosuggestions.git ${ZSH}/.oh-my-zsh/custom/plugins/zsh-autosuggestions`
7. Install zsh-syntax-highlighting. `$ git clone --depth=1 https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH}/custom/plugins/zsh-syntax-highlighting`
8. Find and edit the following lines in `~/.zshrc`:

   | Option      | New Value                                                                            |
   | ----------- | ------------------------------------------------------------------------------------ |
   | `ZSH_THEME` | `powerlevel10k/powerlevel10k`                                                        |
   | `plugins`   | `(command-not-found gh git python sudo zsh-autosuggestions zsh-syntax-highlighting)` |

9. Edit `.zshrc` and add the following lines at the end of the file:[^2]
   ```zsh
   export LANG=en_US.UTF-8  # Set language environment variable.
   export LESS="--no-init --quit-if-one-screen -R"  # Causes `less` to just write to stdout if the text can be viewed without scrolling.
   export GPG_TTY=$TTY  # Fix GPG "gpg failed to sign data" error.
   ```
10. (_Optional_) Install Powerlevel10k's [recommended font](https://github.com/romkatv/powerlevel10k#meslo-nerd-font-patched-for-powerlevel10k).
11. Reload the terminal. `$ source ~/.zshrc`
12. Follow the on-screen instructions to set up Powerlevel10k.

[^1]: If you encounter an error `chsh: <zsh-path>: non-standard shell`, add the path to `/etc/shells`. `$ echo "$(which zsh)" >> /etc/shells`. In Termux, you might have to use `$ chsh -s zsh` instead.
[^2]: It is also recommended that you export the `EDITOR` and `VIEWER` environment variables.

---

**References**:

- [GitHub | ohmyzsh/ohmyzsh](https://github.com/ohmyzsh/ohmyzsh)
- [GitHub | romkatv/powerlevel10k](https://github.com/romkatv/powerlevel10k)

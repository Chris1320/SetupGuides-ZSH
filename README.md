# Zsh

> "The [Z shell](https://www.zsh.org/) is a Unix shell that can be used as an interactive login shell and as a command interpreter for shell scripting. Zsh is an extended Bourne shell with many improvements, including some features of Bash, ksh, and tcsh."

\- [Wikipedia](https://en.wikipedia.org/wiki/Z_shell)

## Customization Features

This customization guide will do the following changes:

- Install zsh, wget, and git packages.
- Change your terminal shell to [zsh](https://www.zsh.org/).
- Install [oh-my-zsh](https://ohmyz.sh/), a zsh configuration manager.
- Install [powerlevel10k](https://github.com/romkatv/powerlevel10k), a custom theme for zsh.
- Install [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions), a plugin that will auto suggest commands based on your zsh history.
- Install [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting), a plugin that will provide syntax highlighting in your zsh shell.

## Automatic Installation & Customization

Download and run the install script using either of the following commands:

- Using *wget*: `$ bash <(wget -q -O - "https://raw.githubusercontent.com/SetupGuides/ZSH/main/install")`
- Using *curl*: `$ bash <(curl -sSf "https://raw.githubusercontent.com/SetupGuides/ZSH/main/install")`

To disable changing the default shell and opening ZSH, run with `--install-only` flag. Example:

`$ bash <(curl -sSf "https://raw.githubusercontent.com/SetupGuides/ZSH/main/install") --install-only`

## Manual Installation & Customization

> [***NOTE***] This guide assumes that you are using `apt` as your package manager.

1. Update apt and install zsh, wget, and git if not yet installed. `$ sudo apt update && sudo apt install --upgrade zsh wget git`
2. Change the shell to zsh. `$ chsh -s $(which zsh)`[^1]
3. Reload your terminal.
4. Download Oh-My-Zsh. `$ sh -c "$(wget -q -O - https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`
5. Install powerlevel10k. `$ git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH}/custom/themes/powerlevel10k`
6. Install zsh-autosuggestions. `$ git clone --depth=1 https://github.com/zsh-users/zsh-autosuggestions.git ${ZSH}/.oh-my-zsh/custom/plugins/zsh-autosuggestions`
7. Install zsh-syntax-highlighting. `$ git clone --depth=1 https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH}/custom/plugins/zsh-syntax-highlighting`
8. Find and edit the following lines in `~/.zshrc`:

    | Option          | New Value                                                                            |
    |-----------------|--------------------------------------------------------------------------------------|
    | `ZSH_THEME`     | `powerlevel10k/powerlevel10k`                                                        |
    | `plugins`       | `(command-not-found gh git python sudo zsh-autosuggestions zsh-syntax-highlighting)` |

9. Edit `.zshrc` and add the following lines at the end of the file:[^2]
    ```zsh
    export LANG=en_US.UTF-8  # Set language environment variable.
    export LESS="--no-init --quit-if-one-screen -R"  # Causes `less` to just write to stdout if the text can be viewed without scrolling.
    export GPG_TTY=$TTY  # Fix GPG "gpg failed to sign data" error.
    ```
10. (*Optional*) Install Powerlevel10k's [recommended font](https://github.com/romkatv/powerlevel10k#meslo-nerd-font-patched-for-powerlevel10k).
11. Reload the terminal. `$ source ~/.zshrc`
12. Follow the on-screen instructions to set up Powerlevel10k.

[^1]: If you encounter an error `chsh: <zsh-path>: non-standard shell`, add the path to `/etc/shells`. `$ echo "$(which zsh)" >> /etc/shells`. In Termux, you might have to use `$ chsh -s zsh` instead.
[^2]: It is also recommended that you export the `EDITOR` and `VIEWER` environment variables.

-----

**References**:

- [GitHub | ohmyzsh/ohmyzsh](https://github.com/ohmyzsh/ohmyzsh)
- [GitHub | romkatv/powerlevel10k](https://github.com/romkatv/powerlevel10k)

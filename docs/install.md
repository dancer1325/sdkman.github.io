## -- based on -- OS
### | UNIX 

* == | 
  * macOS,
  * Linux 
  * Windows + WSL

* compatible -- with -- Bash & ZSH shells

* steps
  * `curl -s "https://get.sdkman.io" | bash`
    * | macOs, 👀modify
      * "$HOME/.bash_profile"
      * "$HOME/.zshrc"👀
  * `source "$HOME/.sdkman/bin/sdkman-init.sh"`
    * specified -- as -- on-screen instructions
  * `sdk version`
    * check the installation

### | Windows

* TODO:For Windows, there are two installation routes:

1. **WSL Approach**: Install Windows Subsystem for Linux (WSL) before attempting
   SDKMAN installation. A basic toolset (bash, zip, unzip, curl) is necessary.
   Most times, it works out of the box.
2. **Git Bash Solution**: If you use Git Bash for Windows, you'll need to
   supplement it with MinGW to have the required toolset for SDKMAN. There are
   some issues with this approach, but it works for the most part.

:::note

Remember, SDKMAN requires a bash environment to run. On Windows, it can't be
natively installed; you need WSL or MSYS+MinGW. We no longer support Cygwin.

:::

## Beta channel

* steps to leave the beta channel,
  * | ["~/.sdkman/etc/config"](usage.md#configuration----sdkmanetcconfig---)
    * set `sdkman_beta_channel=false`
    * `sdk selfupdate force`

## Uninstallation

* steps
  1. 
     ```shell
     # 1. back up
     # OPTIONALLY, BUT recommended
     tar zcvf ~/sdkman-backup_$(date +%F-%kh%M).tar.gz -C ~/ .sdkman
     
     # 2. remove the installation
     rm -rf ~/.sdkman
     ```

  2. | ".bashrc", ".zshrc", ".bash_profile", ...
     * remove initialization snippet
        ```shell
        #THIS MUST BE AT THE END OF THE FILE FOR SDKMAN TO WORK!!!
        [[ -s "/home/dudette/.sdkman/bin/sdkman-init.sh" ]] && source "/home/dudette/.sdkman/bin/sdkman-init.sh"
        ```

## Install SDKMAN | custom location

* ⚠️requirements⚠️
  * you have FULL access rights
  * the folder does NOT exist

```shell
export SDKMAN_DIR="/usr/local/sdkman" && curl -s "https://get.sdkman.io" | bash
```

## Install without modifying shell config

* TODO: And for installs on CI where shell config modification isn't appropriate, add
`rcupdate=false` as a parameter when downloading the installer:

```shell
curl -s "https://get.sdkman.io?rcupdate=false" | bash
```

## CI Mode

```shell
curl -s "https://get.sdkman.io?ci=true" | bash
```

* uses
  * | CI/CD pipelines 

* allows
  * answers ALL installation prompts
    * Reason:🧠thanks to `sdkman_auto_answer=true`🧠
  * disables colored output for cleaner logs
    * Reason:🧠thanks to `sdkman_colour_enable=false`🧠
  * turns off the self-update feature
    * Reason:🧠
      * prevent unexpected updates
      * thanks to `sdkman_selfupdate_feature=false`🧠

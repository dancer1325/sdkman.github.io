## Installing an SDK

### Latest Stable

* `sdk install java`
  * install the **latest stable** version of Java JDK
  * ⚠️AUTOMATICALLY, set it as **default**⚠️

### Specific Version

* `sdk install specifySomeSdk specifyTheVersion`
  * _Example:_ `sdk install scala 3.4.2`

### Install Local Version(s)

* 👀ALLOWED |
  * snapshot version
  * local installation👀

* `sdk install specifySomeSdk specifyTheVersion specifyTheLocation`
  * _Example:_ `sdk install java 17-zulu /Library/Java/JavaVirtualMachines/zulu-17.jdk/Contents/Home`
  * `specifySomeSdk specifyTheVersion`
    * ⚠️MUST be != EXISTING | running `sdk list`⚠️

## Remove an installed version

* `sdk uninstall specifySomeSdk specifyTheVersion`
  * _Example:_ `sdk uninstall scala 3.4.2`
  * ❌if you remove a local version NOT remove the local installation❌

## List Candidates

* `sdk list`
  * 👀list the AVAILABLE candidates👀
    * name + current stable default version + website URL + description + way to install command
    * Reason:🧠 piped to `less`🧠
    * ⚠️!= [list versions](#list-versions)⚠️

## List Versions

* `sdk list specifySomeSdk`
  * list AVAILABLE, LOCAL + INSTALLED + CURRENT candidate versions 
  * _Example:_ `sdk list groovy`

    ```shell
    ================================================================================
    Available Groovy Versions
    ================================================================================
    > * 2.4.4                2.3.1                2.0.8                1.8.3
    2.4.3                2.3.0                2.0.7                1.8.2
    2.4.2                2.2.2                2.0.6                1.8.1
    2.4.1                2.2.1                2.0.5                1.8.0
    2.4.0                2.2.0                2.0.4                1.7.9
    2.3.9                2.1.9                2.0.3                1.7.8
    2.3.8                2.1.8                2.0.2                1.7.7
    2.3.7                2.1.7                2.0.1                1.7.6
    2.3.6                2.1.6                2.0.0                1.7.5
    2.3.5                2.1.5                1.8.9                1.7.4
    2.3.4                2.1.4                1.8.8                1.7.3
    2.3.3                2.1.3                1.8.7                1.7.2
    2.3.2                2.1.2                1.8.6                1.7.11
    2.3.11               2.1.1                1.8.5                1.7.10
    2.3.10               2.1.0                1.8.4                1.7.1
    
    ================================================================================
    + - local version
    * - installed
    > - currently in use
    ================================================================================
    ```

## Use Version | CURRENT terminal

* `sdk use specifySomeSdk specifyTheVersion`
  * _Example:_ `sdk use scala 3.4.2`

## Default Version

* == ⚠️switch version | ALL terminals⚠️
* `sdk default specifySomeSdk specifyTheVersion`
  * _Example:_ `sdk default scala 3.4.2`

## Current Version(s)

* `sdk current specifySomeSdk`
  * check CURRENTLY used SDK candidate's version
  * _Example:_ `sdk current java`

* `sdk current`
  * check CURRENTLY ALL SDK's version

## Env Command -- `sdk env` --

* uses
  * use SPECIFIC JDK or SDK / SPECIFIC project

* 👀configured -- through -- ".sdkmanrc" | your project👀

* steps
  * `sdk env init`
    * generate AUTOMATICALLY the ".sdkmanrc"

        ```shell
        # Enable auto-env -- through the -- `sdkman_auto_env` config
        # key=value pairs -- about -- SDKs / 
        #   1. prepopulated -- with -- CURRENT established SDK versions
        java=21.0.4-tem
        ```
  * if you want to use | your project -> `sdk env`
    * VALID | CURRENT shell
      * ⚠️if you want to reset | CURRENT shell -> `sdk env clear`⚠️
  * if you miss some SDKs specified | project's ".sdkmanrc" -> `sdk env install`

* if you want to be ⚠️notified⚠️ IMMEDIATELY | `cd` into a directory -> set the [`sdkman_auto_env=true`](#configuration----sdkmanetcconfig---)

## Upgrade Version(s)

* `sdk upgrade specifySomeSdk`
  * check if `specifySomeSdk` is out of date 
  * _Example:_

    ```shell
    sdk upgrade springboot
    
    Upgrade:
    springboot (1.2.4.RELEASE, 1.2.3.RELEASE < 3.3.1)
    ```

* `sdk upgrade`
  * check BETWEEN ALL Candidates which are outdated

  ```shell
  $ sdk upgrade
  
  Upgrade:
  gradle (2.3, 1.11, 2.4, 2.5 < 8.9)
  grails (2.5.1 < 6.2.0)
  springboot (1.2.4.RELEASE, 1.2.3.RELEASE < 3.3.1
  ```

## SDKMAN! Version

* `sdk version`
  * check CURRENT SDKMAN!'s
    * script versions
    * native versions

## Offline Mode

* TODO:
Initially called _Aeroplane Mode_, this allows SDKMAN! to function when working
offline. It has a parameter that can be passed to _enable_ or _disable_ the
offline mode.

```shell
sdk offline enable

Forced offline mode enabled.
```

```shell
sdk offline disable

Online mode re-enabled!
```

When operating in **offline** mode, most commands will still work even though
they will operate in a scaled down capacity. An example is the list command,
which will only display the currently installed and active version(s):

```shell
sdk list groovy

------------------------------------------------------------
Offline Mode: only showing installed groovy versions
------------------------------------------------------------
> 2.4.4
* 2.4.3
------------------------------------------------------------
* - installed
> - currently in use
------------------------------------------------------------
```

The offline mode will also be disabled/enabled automatically when the internet
becomes available/unavailable. Naturally, commands that require internet
connectivity will not function but give a warning.

## Self-Update

Installs a new version of SDKMAN! if available.

```shell
sdk selfupdate
```

If no new version is available an appropriate message will be displayed.
Re-installation may be forced by passing the force parameter to the command:

```shell
sdk selfupdate force
```

Automatic daily checks for new versions of SDKMAN! will also be performed on the
behalf of the user.

## Update

Periodically SDKMAN! requires a refresh to become aware of new (or removed)
candidates. When candidate metadata has potentially grown stale, a warning is
displayed with instruction on how to update. By simply running the following
command, the candidate cache will be refreshed and new candidates will become
available for installation:

```shell
WARNING: SDKMAN is out-of-date and requires an update.

sdk update

Adding new candidates(s): kotlin
```

## Flush

It should rarely be necessary to flush SDKMAN!'s local state. The flush command
helps with this, so you don't need to delete any directories. **Manually
deleting directories like the `.sdkman/tmp` directory will break SDKMAN! Always
use the `flush` command instead!**

```shell
sdk flush
```

## Home

When using SDKMAN in scripts, it is often useful to get the absolute path of
where an SDK resides (similar to how the `java_home` command works on macOS).
For this we have the `home` command.

```shell
sdk home java 21.0.4-tem

/home/myuser/.sdkman/candidates/java/21.0.4-tem
```

## Help

You can get basic help by running the following command:

```shell
sdk help
```

This should render a useful top-level help page. You can add qualifier to this
command to get help about a specific sub-command.

```shell
sdk help install
```

## Configuration -- "~/.sdkman/etc/config" --

* ways to edit
  * manually
  * -- via -- `sdk config`

* AVAILABLE configurations

    ```shell
    # sdkman non-interactive
    #   | CI environments, set true 
    sdkman_auto_answer=true|false
    
    # check for newer versions and prompt for update
    sdkman_selfupdate_feature=true|false
    
    # disables SSL certificate verification
    # https://github.com/sdkman/sdkman-cli/issues/327
    # HERE BE DRAGONS....
    sdkman_insecure_ssl=true|false
    
    # configure curl timeouts
    sdkman_curl_connect_timeout=5
    sdkman_curl_continue=true
    sdkman_curl_max_time=10
    
    # subscribe -- to the -- beta channel
    sdkman_beta_channel=true|false
    
    # enable verbose debugging
    sdkman_debug_mode=true|false
    
    # enable colour mode
    sdkman_colour_enable=true|false
    
    # enable AUTOMATIC env
    sdkman_auto_env=true|false
    
    # enable bash or zsh auto-completion
    sdkman_auto_complete=true|false
    ```

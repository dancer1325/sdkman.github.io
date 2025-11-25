## How has it been created?
* -- via -- IDE as Java project

## Env Command -- `sdk env` --
### steps
* follow the steps
#### `sdk env init`
* create AUTOMATICALLY [".sdkmanrc"](.sdkmanrc)
* `java --version`
  * check version == default one
#### if you want to use | your project -> `sdk env`
* `java --version`
  * == [".sdkmanrc"](.sdkmanrc)'s specified
#### ⚠️if you want to reset | CURRENT shell -> `sdk env clear`⚠️
* `java --version`
  * == default one
#### if you miss some SDKs specified | project's ".sdkmanrc" -> `sdk env install`
* PREVIOUSLY, 
  * add a NEW one NOT downloaded | project's ".sdkmanrc"
### if you want to be ⚠️notified⚠️ IMMEDIATELY | `cd` into a directory -> set the [`sdkman_auto_env=true`](#configuration----sdkmanetcconfig---)
* open a NEW terminal | this project
  * check the warning message notifying to install
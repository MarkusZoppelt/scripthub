# ScriptHub

> [!IMPORTANT]
>
> We have not vetted any of the scripts in ScriptHub and (currently) they can
> do anything they want to your computer.
>
> We fully intend to add sandboxing and user reporting, but you have found
> ScriptHub super early in its life so you must practice caution in your usage.
>
> All scripts can be read in advance via https://hub.pkgx.sh


## Adding your Scripts to [hub.pkgx.sh][ScriptHub]

1. Fork [pkgxdev/scripthub]
   > 🚨 Forks of forks will not be indexed! 🚨
2. Add scripts to `./scripts/`
   * Use any shell or scripting language you like
   * Scripts do not need to use a [`pkgx` shebang]
   * Scripts do not have to be made executable *but we recommend it*
3. **Optional Step** Rewrite the README so there is a `## script-name` section
   * The paragraph after the `##` will be the scripthub description
   * A `### Usage` section will be listed to help users use your script
   * If you don’t provide usage then at some point we will use AI to try to
     generate it. Better you add it yourself tho right?
4. Push to your fork
   > Do not create a pull request, *we index the fork graph!*
5. Wait a bit and then check https://hub.pkgx.sh

### Debugging Scripts

You can easily test your scripts before publishing:

```sh
$ chmod +x scripts/my-script
$ scripts/my-script
```

### Example Fork

https://github.com/mxcl/scripthub

&nbsp;


## Using the Scripts

Once your scripts are visible at [ScriptHub] they can be used with the
ScriptHub cli `shx`:

```sh
$ shx your-script-name-without-extension
```

> If someone already took that name then you can still use it via:
>
> ```sh
> $ shx username/script
> ```

Notably, there is no secret sauce; users can just cURL the script and run it
directly via `pkgx`:

```sh
$ curl -O https://raw.githubusercontent.com/mxcl/scripthub/main/scripts/stargazer
$ pkgx ./stargazer
```

Even `pkgx` isn’t required, they can source the dependencies themselves and
run the script manually:

```sh
$ bash ./stargazer
# ^^ they will need to read the script to determine deps and interpreter
```

Hackers can use your script without installing `pkgx` first via our cURL
one-liner. This executes the script but doesn’t install pkgx or any other
pkgs.

```sh
sh <(curl https://pkgx.sh) shx your-script-name
```

Updates are fetched automatically, there is no versioning at this time.


[pkgxdev/scripthub]: https://github.com/pkgxdev/scripthub
[`pkgx` shebang]: https://docs.pkgx.sh/scripts
[ScriptHub]: https://hub.pkgx.sh
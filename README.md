CodiMD-Sandstorm
===

CodiMD on sandstorm

base on hackmdio/codimd (2.0.0)

More info: https://github.com/hackmdio/codimd

## Something different between CodiMD-Sandstorm and CodiMD

- Using `Anonymous - (Date.ISOString)` as user display name and `x-sandstorm-tab-id` as user profile id to create user when user is not logged in sandstorm.
  > To disable this feature, you need to modify `.sandstorm/launcher.sh`, set `CMD_ENABLE_ANONYMOUS_USER` to `false`

- Using `winston-sandstorm` replace `winston` as an dependency

    Because `process.memoryUsage()` can't be executed on sandstorm. We fork `winston` package, remove usage of `process.memoryUsage()` and pack an new package  `winston-sandstorm` upload to npm
- Link of image upload (which upload to filesystem) will be relative path instead of uri
- Using `multer` replace `formidable`

    Prevent randomly failure of image upload
- Single note per grain
    - If logged on sandstorm, auto login into CodiMD and find or create note then redirect to show it.
    - Otherwise, show note if note is exists or redirect 404 not found page
    - Remove `New` button

        To disable single note per grain(i.e. behavior as CodiMD default), remove following line on `launcher.sh`
        ```
        export CMD_SINGLE_NOTE=true
        ```
- Remove `Publish` button
- Default permission are `freely`

    To using CodiMD default value `editable`, remove following line on `launcher.sh` and rebuild it
    ```
    export CMD_DEFAULT_PERMISSION=freely
    ```
- Hidden export on menu
- Add print mode
- Unsupported on Internet Explore

## License

**License under AGPL.**

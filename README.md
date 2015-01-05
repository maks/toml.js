TOML.js
=======

Javascript implementation of a [TOML](https://github.com/mojombo/toml) parser. Browser-compatible.

Supports TOML v0.1, although the parser is more forgiving than the spec.

### What is TOML?

TOML is the drunken brainchild of Tom Preston-Werner, a INI-inspired minimal alternative to YAML for configuration files.

    # This is a TOML document. Boom.

    title = "TOML Example"

    [owner]
    name = "Tom Preston-Werner"
    organization = "GitHub"
    bio = "GitHub Cofounder & CEO\nLikes tater tots and beer."
    dob = 1979-05-27T07:32:00Z # First class dates? Why not?

This becomes the object:

    {
        title: "TOML Example",
        owner: {
            name: "Tom Preston-Werner",
            bio: "Github Cofounder & CEO\nLikes tater tots and beer.",
            dob: [object Date]
        }
    }

Values are interpreted as `String`, `Number`, `Date`, `Array` and `Object` instances.

### Install

    npm install tomljs

### Use

    var fs   = require('fs')
      , toml = require('toml2')
      , file = fs.readFileSync('config.toml').toString()

    var config = toml(file)

### Build

    git clone https://github.com/ricardobeat/toml.js.git
    npm install
    npm run-script watch

See `Cakefile` for the build/watch tasks.

### Performance

Benchmark using `test/test.toml`:

    TOMLjs: 5ms
    toml: 8ms (fails to parse the key 'false')
    toml-parser: 17ms (fails on deeply nested keys)

### Test

Run `npm test` or `mocha` on the root folder.

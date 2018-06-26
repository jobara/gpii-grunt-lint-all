# gpii-grunt-lint-all

This grunt plugin provides a combined rollup command that runs all GPII lint checks. To add it to your package, use a
command like:

```shell
npm install gpii-grunt-lint-all --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```javascript
grunt.loadNpmTasks("gpii-grunt-lint-all");
```

Please note, as this package provides default configuration options for many commands, if you wish to override options
safely, your `Gruntfile.js` should load this package's tasks first, and then merge your own options, as shown in the
following example:

```javascript
"use strict";
grunt.loadNpmTasks("gpii-grunt-lint-all");
grunt.config.merge({
    eslint: {
        js: {
            src: ["tasks/*.js", "tests/**/*.js", "./*.js"]
        },
        md: {
            src: [ "./*.md"]
        }
    },
    jsonlint: {
        src: ["./*.json"]
    },
    json5lint: {
        src: ["./*.json5"]
    },
    mdjsonlint: {
        src: ["./*.md"]
    },
    markdownlint: {
        src: ["./*.md"]
    }
});
```

Once you have installed the plugin and updated your `Gruntfile.js`, you should be able to run the `lint-all` command from
the root of your repository, as in `grunt lint-all`.

## Configuring Individual Checks

This plugin is a rollup that calls a range of individual checks.  All checks support the standard `src` array that
defines which material should be linted.  For more information about the individual checks and links to their
documentation, see below:

| Task         | Description | Documentation |
| ------------ | ----------- | ------------- |
| eslint       | Run both the `eslint:js` and `eslint:md` tasks (see below). | See below. |
| eslint:js    | Check the validity and formatting of Javascript files. | [fluid-grunt-eslint](https://github.com/fluid-project/fluid-grunt-eslint) |
| eslint:md    | Check the validity and formatting of Javascript code blocks in Markdown files. | [eslint-plugin-markdown](https://github.com/eslint/eslint-plugin-markdown) |
| json5lint    | Check the validity of JSON5 files. | [fluid-grunt-json5lint](https://github.com/fluid-project/fluid-grunt-json5lint) |
| jsonlint     | Check the validity and formatting of JSON files. | [grunt-jsonlint](https://github.com/brandonramirez/grunt-jsonlint) |
| markdownlint | Check the formatting of Markdown files. | [grunt-markdownlint](https://github.com/sagiegurari/grunt-markdownlint) |
| mdjsonlint   | Check the validity and formatting of JSON code blocks within Markdown files. | [gpii-grunt-mdjson-lint](https://github.com/GPII/gpii-grunt-mdjson-lint) |

Please note that many of the above checks use our standard ESLint configuration, which is available in the
[eslint-config-fluid](https://github.com/fluid-project/eslint-config-fluid).  You will need to follow the installation
instructions in that package before you run many of the above checks.
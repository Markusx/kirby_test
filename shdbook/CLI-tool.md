Showdown comes bundled with a simple CLI tool that let's you run showdown converter from the command line.

## Requirements 
In order to use it you need nodejs installed in your system.


## Simple usage guide

If you install showdown globally with `npm install showdown -g`, you can access the CLI tool help by typing in the command line:

```sh
showdown -h
```

A simple usage example would be:

```sh
showdown makehtml -i foo.md -o bar.html
```

This command reads `foo.md` and writes the converted html into `bar.html`


## Command: makehtml

This command converts a markdown input into html

```
showdown makehtml [options]
```

Here's a list of options for makehtml command

### Option -i/--input

 + short: -i
 + alias: --input
 + Description: Input source. Usually a md file. If omitted or empty, reads from stdin
 + Examples:
   + `showdown makehtml -i`: Reads from stdin (and outputs to stdout)
   + `showdown makehtml --input foo.md`: Reads from the file foo.md (and outputs to stdout)

### Option -o/--output

 + short: -o
 + alias: --output
 + Description: Output target. Usually a html file. If omitted or empty, writes to stdout
 + Examples:
   + `showdown makehtml -i foo.md -o bar.html`: Reads from the file foo.md and outputs to bar.html


### Option -u/--encoding

 + short: -u
 + alias: --encoding
 + Description: Specifies the input encoding
 + Examples:
   + `showdown makehtml -u UTF8`


### Option -a/--append

 + short: -a
 + alias: --append
 + Description: Append data to output instead of overwriting
 + Examples:
   + `showdown makehtml -a`


### Option -e/--extensions

 + short: -a
 + alias: --append
 + Description: Load the specified extensions. Should be valid paths to node compatible extensions
 + Examples:
   + `showdown makehtml -e ~/twitter.js -e ~/youtube.js`

### Extra options

If you specify any supported showdown options, those will be passed to the converter. For instance, if you want to activate strikethrough support, you can run the following command:

```
showdown makehtml -i foo.md -o bar.html --strikethrough
```

This is the CLI way of doing:

```js
var conv = new showdown.Converter({strikethrough: true});
```

**NOTE:** Please note that all of the "extra options" are ***DISABLED*** by default in the cli tool. This differs from the behavior in node/browser, in which some options, such as ghCodeBlocks, are enabled (for backwards compatibility and historical reasons).
# Customize SwiftGen templates

This document describes how to make your own templates for SwiftGen, so it can generate code more to your liking and code following your own coding conventions. For in depth documentation of the bundled templates, we refer you to the documentation for [each specific template](https://github.com/SwiftGen/templates/tree/master/Documentation).

## Templates files on disk

When you invoke SwiftGen, you can specify templates by name or by path.

### Using a full path

If you use the `--templatePath` (or `-p`) option, you'll need to specify the **full path** to the template you want to use. This allows you to store your templates anywhere you want and name them anyhow you want, but can become quite annoying to type.

### Using a name

When you use the `--template` (or `-t`) option, you only specify a **template name**. SwiftGen then searches a matching template using the following rules (where `<subcommand>` is one of `colors`, `images`, `storyboards` or `strings` depending on the subcommand you invoke):

* It searches for a file named `<name>.stencil` in `~/Library/Application Support/SwiftGen/templates/<subcommand>/`, which is supposed to contain your own custom templates for that particular subcommand.
* If it does not find one, it searches for a file named `<name>.stencil` in `<installdir>/share/swiftgen/templates/<subcommand>` which contains the templates bundled with SwiftGen for that particular subcommand.

For example `swiftgen images -t foo DIR` will search for a template named `foo.stencil` in Application Support, then in `/usr/local/share/SwiftGen/templates/image` (assuming you installed SwiftGen using Homebrew in `/usr/local`)

## List installed templates

The `swiftgen templates` command will list all the installed templates (as YAML output) for each subcommand, both for bundled templates and custom templates.

```bash
$ swiftgen templates
colors:
  custom:
  bundled:
   - swift2
   - swift3
images:
  custom:
  bundled:
   - swift2
   - swift3
storyboards:
  custom:
   - mytemplate
  bundled:
   - swift2
   - swift3
strings:
  custom:
   - mycustomtemplate
  bundled:
   - flat-swift2
   - flat-swift3
   - structured-swift2
   - structured-swift3
```

## Templates Format, Nodes and Filters

Templates in SwiftGen are based on [Stencil](https://stencil.fuller.li/), a template engine inspired by Django and Mustache. The syntax of the templates [is explained in Stencil's documentation](https://stencil.fuller.li/en/latest/templates.html).

Additionally to the [tags and filters](https://stencil.fuller.li/en/latest/builtins.html) provided by Stencil, SwiftGen provides some additional ones, documented in the [StencilSwiftKit framework](https://github.com/SwiftGen/StencilSwiftKit).

## Templates Contexts

When SwiftGen generates your code, it provides a context (a dictionary) with the variables containing what images/colors/strings/… the subcommand did detect, to render your Stencil template using those variables.

A full documentation of the produced context for each command can be found in the [SwiftGenKit documentation](https://github.com/SwiftGen/SwiftGenKit#documentation).

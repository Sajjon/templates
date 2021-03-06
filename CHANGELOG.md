# Templates CHANGELOG

---

## Master

### Bug Fixes

* Fixed `swiftlint` errors for the latest version.  
  [David Jennes](https://github.com/djbe) 
  [#46](https://github.com/SwiftGen/templates/pull/46)
* Images: fixed issue with catalogs that have an empty folder.  
  [David Jennes](https://github.com/djbe) 
  [#51](https://github.com/SwiftGen/templates/pull/51)

### Breaking Changes

* Templates are now organized in subdirectories for each command.  
  [David Jennes](https://github.com/djbe)
  [#13](https://github.com/SwiftGen/templates/issues/13)
* Update templates to use the Stencil built-in `join` filter instead of our own.  
  [David Jennes](https://github.com/djbe)
  [#22](https://github.com/SwiftGen/templates/issues/22)
* Many deprecated templates have been removed, and others have been renamed to reflect new behaviours. We've prepared a migration guide which you can find here: [Documentation/MigrationGuide](https://github.com/SwiftGen/templates/blob/master/Documentation/MigrationGuide.md).  
  [David Jennes](https://github.com/djbe)
  [#47](https://github.com/SwiftGen/templates/issues/47)
* Since Swift 2 is no longer actively supported, we now consider those templates as "legacy" and cannot guarantee that there won't be issues with the generated code.  
  [David Jennes](https://github.com/djbe)
  [#53](https://github.com/SwiftGen/templates/issues/53)

### New Features

* Strings: the templates have been updated to support multiple string tables.  
  [David Jennes](https://github.com/djbe)
  [#49](https://github.com/SwiftGen/templates/issues/49)
* Colors: the templates have been updated to support multiple color palettes.  
  [David Jennes](https://github.com/djbe)
  [#55](https://github.com/SwiftGen/templates/issues/55)

### Internal Changes

* Removed deprecated variables. See [SwiftGenKit#5](https://github.com/SwiftGen/SwiftGenKit/issues/5) for more information.   
  [David Jennes](https://github.com/djbe)
  [#45](https://github.com/SwiftGen/templates/issues/45)
  [#50](https://github.com/SwiftGen/templates/issues/50)
* We can now re-generate the output files used for testing by using the "Generate Output" Xcode scheme.  
  [David Jennes](https://github.com/djbe)
  [#56](https://github.com/SwiftGen/SwiftGenKit/issues/56)

## 1.1.0

### Bug Fixes

* Fixed `swiftlint` warnings in generated color extensions.  
  [Roman Laitarenko](https://github.com/evil159) 
  [#32](https://github.com/SwiftGen/templates/pull/32)
* The storyboards macOS swift3 template was missing the "current target" module ignore code.  
  [@djbe](https://github.com/djbe)
  [#27](https://github.com/SwiftGen/templates/issues/27)
* Fix the `images` templates so that they work on watchOS again.  
  [David Jennes](https://github.com/djbe)
  [SwiftGen/SwiftGen#275](https://github.com/SwiftGen/SwiftGen/issues/275)
  [#30](https://github.com/SwiftGen/SwiftGenKit/issues/30)

### New Features

* More variables have been deprecated, while new variables have been added. See [SwiftGenKit#5](https://github.com/SwiftGen/SwiftGenKit/issues/5) for more information.   
  [David Jennes](https://github.com/djbe)
  [#28](https://github.com/SwiftGen/templates/issues/28)
  [#39](https://github.com/SwiftGen/templates/issues/39)
  [#43](https://github.com/SwiftGen/templates/issues/43)

### Internal Changes

* Switch from Travis CI to Circle CI, clean up the Rakefile in the process.  
  [David Jennes](https://github.com/djbe)
  [#24](https://github.com/SwiftGen/SwiftGenKit/issues/24)
  [#40](https://github.com/SwiftGen/SwiftGenKit/issues/40)
* Disable SwiftLint `conditional_returns_on_newline` in the font template.  
  [Tom Baranes](https://github.com/tbaranes)
  [#33](https://github.com/SwiftGen/templates/pull/33)
* Updated templates to use Stencil 0.9.0 features, such as for loops with a where condition.  
  [David Jennes](https://github.com/djbe) 
  [#42](https://github.com/SwiftGen/templates/issues/42)

## 1.0.0

_The templates tagged with this version are the ones embedded in SwiftGen 4.2._

### Internal Changes

* Initial tagging of templates as part of being split in their own repository.  
* Templates are now linted and unit-tested, to ensure the code generated compiles properly.  
  [David Jennes](https://github.com/djbe)
  [#5](https://github.com/SwiftGen/templates/issues/5)
  [#6](https://github.com/SwiftGen/templates/issues/6)
  [#15](https://github.com/SwiftGen/templates/pull/15)
  [#16](https://github.com/SwiftGen/templates/pull/16)

### Bug Fixes

* Use `escapeReservedKeywords` in all templates — to ensure compilation even for scenes named with a reserved keyword.  
  [David Jennes](https://github.com/djbe)
  [#3](https://github.com/SwiftGen/templates/issues/3)
  [#14](https://github.com/SwiftGen/templates/pull/14)
* Storyboards templates don't `import` your app module anymore, removing that annoying warning.  
  [David Jennes](https://github.com/djbe)
  [#19](https://github.com/SwiftGen/templates/pull/19)
  * It works by checking the environment variable `PRODUCT_MODULE_NAME`, which is automatically injected by Xcode if you run `swiftgen` as part of a Script Build Phase in your Xcode project.
  * If you don't use `swiftgen` in a Script Build Phase of your Xcode project but manually in the terminal, you can instead use  `swiftgen storyboards --param module=YourAppModuleName …` when invoking SwiftGen to inject it manually instead.

### New Features

* Use an explicit bundle parameter to support frameworks for all templates.  
  [@NachoSoto](https://github.com/NachoSoto)
  [David Jennes](https://github.com/djbe)
  [SwiftGen/SwiftGen#255](https://github.com/SwiftGen/SwiftGen/pull/255)
  [#17](https://github.com/SwiftGen/templates/pull/17)
* Use `enum` instead of `struct` for namespacing in all templates.  
  [David Jennes](https://github.com/djbe)
  [#7](https://github.com/SwiftGen/templates/issues/7)
* Reworked templates to get rid of deprecated Stencil variables.  
  [David Jennes](https://github.com/djbe)
  [#8](https://github.com/SwiftGen/templates/issues/8)
  [#9](https://github.com/SwiftGen/templates/issues/9)


## Pre-1.0.0

_See SwitftGen's own CHANGELOG pre SwiftGen 4.2 version, before the refactoring that led us to split the code in frameworks_

### Deprecations

Note that in preparation for the upcoming SwiftGen 5.0, some variables available in the SwiftGen's Stencil templates have been deprecated and will be renamed. To prepare for SwiftGen 5.0, **we strongly advise to migrate your custom templates so they use the new variables** (already available in SwiftGen 4.2 / SwiftGenKit 1.0.1) instead of the old ones, so that they will continue to work in SwiftGen 5.0

See [the migration guide in SwiftGen's wiki](https://github.com/SwiftGen/SwiftGen/wiki/Migration-Guides).

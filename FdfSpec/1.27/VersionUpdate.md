# Document Change Notice

Change Document: EDK II Flash Definition (FDF) File Specification

(http://github.com/tianocore-docs/Docs)

Current Document Revision: 1.26

Target Revision: 1.27

DCN Date: 29 Jan 2016

### Summary
Changes the ```FDF_SPECIFICATION``` value from ```0x0001001A``` to ```0x0001001B``` or ```1.27```

# 2 FDF Design Discussion

~~This revision of the specification adds support for multiple EDK II Packages directories outside of the WORKSPACE. FDF files that use this feature must use the new ```FDF_SPECIFICATION = 0x00010019``` in the ```[Defines]``` section. Older FDF files do not need to update the FDF_SPECIFICATION value.
~~

> This revision of the specification adds support for multiple binary files in an FV ```FILE RAW``` statement. FDF files that use this feature must use the new ```FDF_SPECIFICATION = 0x0001001B``` in the ```[Defines]``` section. Older FDF files do not need to update the ```FDF_SPECIFICATION``` value.

## 3.4 [Defines] Section
This is an optional section. This section, if present, must be the first section following comment blocks at the beginning of the file.

**Summary**

This section describes the defines section content in the FDF files. This file can be created by a developer and is an input to the EDK II build tool parsing utilities. Elements may appear in any order within this section.

~~The code for this version of the FDF specification is "0x0001001A" and new versions of this specification must increment the minor (001A) portion of the specification code for backward compatible changes, and increment the major number for non-backward compatible specification changes.~~

~~This revision of the specification adds FMP Capsule support. Any FDF file that uses this feature must use the 0x0001001A FDF_SPECIFICATION value. Older FDF files that do not use this feature do not need to update the value.~~

> The code for this version of the FDF specification is "0x0001001B" and new versions of this specification must increment the minor (001B) portion of the specification code for backward compatible changes, and increment the major number for non-backward compatible specification changes.

> This revision of the specification adds support for multiple binaries in an FV or Capsule ```RAW FILE``` statement. Any FDF file that uses this feature must use the value ```0x0001001B``` in the ```FDF_SPECIFICATION``` statement. Older FDF files that do not use this feature do not need to update the value.

Conditional statements may be used anywhere within this section.

**Parameters***

|  |  |
| --: | :---- |
| *Expression* | |
| | Refer to the EDK II Expression Syntax Specification for more information. |
| *FDF_VERSION* | |
| | The version number for this flash definition; the value is not used by build tools, but the version element is provided for user tracking capabilities that may be used by other user interface tools. |
| *FDF_SPECIFICATION* | |
| | ~~For this specification, the version value is 0x0001001A. Tools that process this version of the FDF file can successfully process earlier versions of the FDF files (this is a backward compatible update). If an FDF file with an earlier version of the ```FDF_SPECIFICATION``` is modified to use the FMP Payload section and FMP Capsule definitions, the version value should be updated to 0x0001001A. There is no requirement to change existing entries if no other content changes. This value may also be specified as decimal value, such as 1.26.~~ |
| | For this specification, the version value is ```0x0001001B```. Tools that process this version of the FDF file can successfully process earlier versions of the FDF files (this is a backward compatible update). If an FDF file with an earlier version of the ```FDF_SPECIFICATION``` is modified to use new features, the version value should be updated to ```0x0001001B```. There is no requirement to change existing entries if no other content changes. This value may also be specified as decimal value, such as 1.27. |

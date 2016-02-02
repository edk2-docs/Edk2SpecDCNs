# Document Change Notice


Change Document: EDK II Package Declaration (DEC) File Specification

(http://github.com/tianocore-docs/Docs)

Current Document Revision: 1.25

Target Revision: 1.26

DCN Date: 27 Jan 2016

### Summary
Changes the ```DEC_SPECIFICATION``` value from ```0x00010019``` to ```0x0001001A``` or ```1.26```

## 2.4 [Defines] Usage

The DEC_SPECIFICATION of existing DEC files does not need to be updated unless
content in the file has been updated to match new content specified by this
revision of the specification. Additionally, the package's version major number
may change. Minor changes require incrementing the package's version minor 
number. The ```PACKAGE_UNI_FILE``` entry points to a Unicode file containing 
localization strings. The use of the ```#include``` statement in this file is 
prohibited. The file path (if present) is relative to the directory containing
the DEC file.

The parsing utilities process any local symbol assignments defined in this
section. Note that the sections are processed in the order listed in the DEC
file, and later assignments of these local symbols override previous
assignments.

This section will use only one section header:

```ini
[Defines]
```

The format for entries in this section is:
```C
Name = Value
```

The following is an example of this section.
```ini
[Defines]
~~DEC_SPECIFICATION = 0x00010019~~
  DEC_SPECIFICATION = 0x0001001A
  PACKAGE_NAME = MdePkg
  PACKAGE_GUID = 1E73767F-8F52-4603-AEB4-F29B510B6766
  PACKAGE_VERSION = 1.02
  PACKAGE_UNI_FILE = MdePkg.uni
```

## 3.4 [Defines] Sections
**Summary**
This describes the ```[Defines]``` section, which is required in all DEC files. This 
file is created during installation of a UEFI distribution package or by the 
developer and is an input to the EDK II build tool parsing utilities. Elements 
may appear in any order within this section.

~~The code for this specification is "00010019" and new versions of this~~
~~specification must increment the minor (0019) portion of the specification code.~~
~~This value may also be specified as a decimal value, 1.25.~~

> The code for this specification is ```0x0001001A``` and new versions of this
> specification must increment the minor (```001A```) portion of the specification code.
> This value may also be specified as a decimal value, ```1.26```.

Existing DEC files are not required to update the ```DEC_SPECIFICATION``` 
version value. This value may be used by tools to identify any new functionality 
introduced by this specification version.

**Parameters**

|     |     |
| --: | :-- |
| *UiNameType* |   |
|  | The ```PACKAGE_NAME``` value may be used for creating directories. |
| *DecimalVersion* |    |
|  | This is a decimal number, and if not specified is assumed to be 0. Alpha characters are not permitted. |
| *SpecVer* |     |
|  | For new DEC files, the version value must be set to ```0x0001001A```. Tools that process this version of the DEC file can successfully process earlier versions of the DEC file (this is a backward compatible update). There is no requirement to change the value in existing DEC files if no other content changes. This may also be specified as decimal value, ```1.26```. |
| *Filename* |    |
|  | Filenames listed in the ```[Defines]``` section must be relative to the directory the DEC file is in. Use of "..", "." and "../" in the directory path is not permitted. Use of an absolute path is not permitted. The file name specified in the ```PACKAGE_UNI_FILE``` entry must be a Unicode file with an extension of .uni, .UNI or .Uni. |

 
~~**Example**~~

**Example 1**
```ini
[DEFINES]
  ~~DEC_SPECIFICATION = 0x00010019~~
  > DEC_SPECIFICATION = 0x0001001A
  PACKAGE_NAME = MdePkg
  ~~PACKAGE_GUID = 5e0e9358-46b6-4ae2-8218-4ab8b9bbdcec~~
  ~~PACKAGE_VERSION = 0.3~~
  > PACKAGE_GUID = 1E73767F-8F52-4603-AEB4-F29B510B6766
  > PACKAGE_VERSION = 1.06
  PACKAGE_UNI_FILE = MdePkg.uni
```

> **Example 2**

```ini
> [DEFINES]
  > DEC_SPECIFICATION = 1.26
  > PACKAGE_NAME = IntelFspPkg
  > PACKAGE_GUID = 444C6CDF-55BD-4744-8F74-AE98B003B955
  > PACKAGE_VERSION = 0.1
```

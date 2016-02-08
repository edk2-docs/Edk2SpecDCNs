# Document Change Notice


Change Document: EDK II Module Information (INF) File Specification

(http://github.com/tianocore-docs/Docs)

Current Document Revision: 1.25

Target Revision: 1.26

DCN Date: 27 Jan 2016

### Summary
Changes the ```INF_VERSION``` value from ```0x00010019``` to ```0x0001001A``` 
or ```1.26```

## 2.4 [Defines] Section

This is a required section.

The [Defines] section of EDK II INF files is used to define variable 
assignments that can be used in later build steps. The INF_VERSION of existing
INF files does not need to be updated unless content in the file has been
updated to match new content specified by this revision of the specification.

Architectural modifiers are not permitted in the [Defines] section.

The parsing utilities process any local symbol assignments defined in this
section. The EDK II parsing utilities will use some of this section's
information for generating AutoGen.c and AutoGen.h files. Note that the
sections are processed in the order listed in the INF file, and later
assignments of these local symbols override previous assignments.

```ini
[Defines]
```

The format for entries in this section is:
```C
Name = Value
```

The following is an example of a driver's ```[Defines]``` section.
```ini
[Defines]
~~INF_VERSION       = 0x00010019~~
> INF_VERSION       = 0x0001001A
  BASE_NAME         = DxeIpl
  FILE_GUID         = 86D70125-BAA3-4296-A62F-602BEBBB9081
  VERSION_STRING    = 1.0
  MODULE_TYPE       = PEIM
  ENTRY_POINT       = PeimInitializeDxeIpl
  MODULE_UNI_FILE   = DxeIpl.uni
```

The following is an example of a library's [Defines] section.

```ini
[Defines]
~~  INF_VERSION      = 1.26~~
>  INF_VERSION      = 1.26
  BASE_NAME        = BaseMemoryLib
  FILE_GUID        = fd44e603-002a-4b29-9f5f-529e815b6165
  MODULE_TYPE      = BASE
  VERSION_STRING   = 1.0
  LIBRARY_CLASS    = BaseMemoryLib
```
## 3.4 [Defines] Section

This is a required section.

**Summary**

This describes the required [Defines] section used in EDK II INF files. This
file is created during installation of a UEFI distribution package or by the
developer and is an input to the new build tool parsing utilities. Elements
may appear in any order within this section.

~~The version for this specification is "```0x00010019```" and new versions
of this specification must increment the minor (```0019```) portion of the
specification code for backward compatible changes, and increment the major
number for non-backward compatible specification changes. This value may
also be specified as a decimal value, 1.25.~~

>The version for this specification is "```0x0001001A```" and new versions
of this specification must increment the minor (```001A```) portion of the
specification code for backward compatible changes, and increment the major
number for non-backward compatible specification changes. This value may
also be specified as a decimal value, ```1.26```.

The ```[Defines]``` section assigns values to the symbols that describe the
component. Some items are emitted to the output makefile, others are used to
create filenames during the build. Some symbols are emitted to the generated
C files.

~~The ```FILE_GUID``` is required for all EDK II modules. This GUID is used to
build the FW volume file list used by build tools to generate the final
firmware volume, as well as processed in some SMM, PEI or DXE ```DEPEX```
statements.~~

> The ```FILE_GUID``` is required for all EDK II modules. This GUID is used to
build the FW volume file list used by build tools to generate the final
firmware volume, as well as processed in some ```SMM, PEI``` or
```DXE DEPEX``` statements.

~~All new EDK II INF files must include one of the following statements: 
```INF_VERSION = 0x00010019 or INF_VERSION = 1.25``` in this section,
where the number varies according to the release of this specification. It
is a HexVersion type, where the ```0x0001``` is the major number, and the 
```0019``` is the minor number. This version of the specification provides
full backward compatibility to all previous versions. This means that tools
that process this version of the specification can also process earlier
versions of EDK II INF files.~~

> All new EDK II INF files must include one of the following statements: 
```INF_VERSION = 0x0001001A``` or ```INF_VERSION = 1.26``` in this section,
where the number varies according to the release of this specification. It
is a ```HexVersion``` type, where the ```0x0001``` is the major number, and
the ```001A``` is the minor number. This version of the specification
provides full backward compatibility to all previous versions. This means
that tools that process this version of the specification can also process
earlier versions of EDK II INF files.


**Parameters**

|     |     |
| --: | :-- |
| *Filename* |   |
|  | Filenames listed in the [Defines] section must be relative to the directory the INF file is in. Use of "..", "." and "../" in the directory path is not permitted. Use of an absolute path is not permitted. The file name specified in the MODULE_UNI_FILE entry must be a Unicode file with an extension of .uni, .UNI or .Uni. |
| *MODULE_TYPE* |    |
|  | Drivers and applications are not allowed to have a ```MODULE_TYPE``` of "```BASE```". Only libraries are permitted to a have a ```MODULE_TYPE``` of "```BASE```". A INF file can be used to specify other binary files types, such as logo images or legacy16 option ROMs. The ```USER_DEFINED``` module type must be used in all cases where the module type is not a member of ```<Edk2ModuleType>```. |
| *INF_VERSION* |     |
|  | ~~For new INF files, the version value must be set to ```0x00010019```. Tools that process this version of the INF file can successfully process earlier versions of the INF file (this is a backward compatible update). There is no requirement to change the value in existing INF files if no other content changes. This may also be specified as decimal value, ```1.25```.~~ |
|  | > For new INF files, the version value must be set to ```0x00010019```. Tools that process this version of the INF file can successfully process earlier versions of the INF file (this is a backward compatible update). There is no requirement to change the value in existing INF files if no other content changes. This may also be specified as decimal value, ```1.25```. |
| *EDK_RELEASE_VERSION* |    |
|  | This optional value may be set to the major/minor number of the EDK II release required for modules to function correctly. |


 
~~**Example**~~

**Example (EDK II Driver)**
```ini
[Defines]
~~  INF_VERSION              = 1.25~~
>  INF_VERSION               = 1.26
  BASE_NAME                  = PlatformAcpiTable
  FILE_GUID                  = 7E374E25-8E01-4FEE-87F2-390C23C606CD
  MODULE_TYPE                = DXE_DRIVER
  VERSION_STRING             = 1.0
  EDK_RELEASE_VERSION        = 0x00020000
  UEFI_SPECIFICATION_VERSION = 0x00020014
  
```

**Example (UEFI Driver)**

```ini
[Defines]
  ~~INF_VERSION = 0x00010019~~
> INF_VERSION = 0x0001001A
  BASE_NAME = Abc
  FILE_GUID = DA87D340-15C0-4824-9BF3-D52286674BEF
  MODULE_TYPE = UEFI_DRIVER
  VERSION_STRING = 1.0
  ENTRY_POINT = AbcDriverEntryPoint
  UNLOAD_IMAGE = AbcUnload
```

**Example (EDK II Library)**

```ini
[Defines]
~~  INF_VERSION   = 1.25~~
>  INF_VERSION    = 1.26
  BASE_NAME       = LzmaCustomDecompressLib
  FILE_GUID       = 22f8406f-43ee-492f-82f5-4e8a1a58e6d2
  MODULE_TYPE     = BASE
  VERSION_STRING  = 1.0
  LIBRARY_CLASS   = CustomDecompressLib
```

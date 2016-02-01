 Document Change Notice

Change Document: EDK II Flash Definition (FDF) File Specification

(http://github.com/tianocore-docs/Docs)

Current Document Revision: 1.26

Target Revision: 1.27

DCN Date: 01 Feb 2016

### Summary
Changes the ```DSC_SPECIFICATION``` value from ```0x0001001A``` to ```0x0001001B``` or ```1.27```

# 2 DSC Overview

~~DSC files that use any new features must use the new DSC_SPECIFICATION = 0x0001001A in the [Defines] section. Older DSC files that do not use any of these features do not need to update the DSC_SPECIFICATION value.
~~

> DSC files that use any new features must use the new DSC_SPECIFICATION = 0x0001001B in the [Defines] section. Older DSC files that do not use any of these features do not need to update the DSC_SPECIFICATION value.

## 2.3 [Defines] Section
**Table 6. EDK II [Defines] Section Elements**

| **Typical Tag Names**  | **Required/Optional** | **Value**  | **Notes** |
| :---- | :---: | :---- | :---- |
| ~~```DSC_SPECIFICATION```~~ | ~~Required~~ | ~~0x0001001A or 1.26~~ | ~~This entry is required for all EDK II DSC files. The value, 0x0001001A matches the 1.26 version of this specification. Build tools must continue to support DSC files that correspond to earlier versions of the document until such time as earlier versions are no longer in use. In order to maintain backward compatibility, this value must only be updated in existing DSC files if other content in the file is updated. This value may also be specified as decimal value, i.e., 1.26.~~ |
| > ```DSC_SPECIFICATION``` | > Required | > 0x0001001B or 1.27 | > This entry is required for all EDK II DSC files. The value, 0x0001001B matches the 1.27 version of this specification. Build tools must continue to support DSC files that correspond to earlier versions of the document until such time as earlier versions are no longer in use. In order to maintain backward compatibility, this value must only be updated in existing DSC files if other content in the file is updated. This value may also be specified as decimal value, i.e., 1.27. |
| &#32; | &#32; | &#32; | &#32; |


## 3.5 [Defines] Section

**Summary**

***Note:*** *Assignments of variables in other sections take precedence over global assignments.*

This section describes the defines section content in the DSC files. This file can be created by a developer and is an input to the EDK II build tool parsing utilities. Elements may appear in any order within this section.

~~This revision of specification does not add new features. New EDK II DSC files must include the statement: DSC_SPECIFICATION = 0x0001001A in this section. Existing DSC files do not need to update the value.~~

> This revision of the specification adds support for specifying a GUID value as a Registry 
Format GUID in addition to a C Format GUID. Any DSC file that uses this feature must use the 0x0001001B DSC_SPECIFICATION value. Older DSC files that do not use this feature do not need to update the value.

Individual items must appear on a single line, they may not span multiple lines.


**Parameters***

|  |  |
| --: | :---- |
| *SpecVal* | |
| | ~~New DSC files or DSC files that get updated to use any of the new features defined in this specification must ensure that the 0x0001001A value is used. The EDK II build system must maintain backward compatibility, therefore, there is no requirement to change existing DSC files if no other content changes. This value may also be specified as a decimal value of 1.26.~~ |
| | > New DSC files or DSC files that get updated to use any of the new features defined in this specification must ensure that the 0x0001001B value is used. The EDK II build system must maintain backward compatibility, therefore, there is no requirement to change existing DSC files if no other content changes. This value may also be specified as a decimal value of 1.27.~~ |
|  |  |


**Example**
```ini
[Defines]
  PLATFORM_NAME = NT32
  PLATFORM_GUID = EB216561-961F-47EE-9EF9-CA426EF547C2
  PLATFORM_VERSION = 0.3
  ~~DSC_SPECIFICATION = 0x0001001A~~
  > DSC_SPECIFICATION = 1.27
  OUTPUT_DIRECTORY = Build/Nt32
  SUPPORTED_ARCHITECTURES = IA32
  BUILD_TARGETS = DEBUG|RELEASE
  RFC_LANGUAGES = "en-us;zh-hans;fr-fr"
  ISO_LANGUAGES = "engchnfra"
  SKUID_IDENTIFIER = SkuTwo|DEFAULT
```

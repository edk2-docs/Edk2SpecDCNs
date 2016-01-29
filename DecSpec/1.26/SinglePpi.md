# Document Change Notice

Change Document: EDK II Package Declaration (DEC) File Specification
(http://github.com/tianocore-docs/Docs)

Current Document Revision: 1.25
New Revision: 1.26

DCN Date: 27 Jan 2016

### Summary

1. Allow use of Registry Format GUID to declarations
2. Adding new reserved comment, ```@SinglePpi```


## 2.8 [Ppis] Usage
This is an optional section.

This section is used to define the GUID Value for PPI C Names.

This section uses one of the following section definitions:

```[Ppis] [Ppis.IA32] [Ppis.X64] [Ppis.IPF] [Ppis.EBC] [Ppis.common] ```

Format for the entries in this section is two fields with an equal “```=```” 
character separating the fields as shown below.
```ini
> # Comment Block
>  PpiCName = Guid Value # Comment
~~PpiCName = {C Format Guid Value} # Comment~~
~~PpiCName = RegistryFormatGUID # Comment~~
```
~~The Comment section can be used to identify the list of supported module types.~~

> A comment block preceding the entry must be used to provide detailed  information, including the
> name of the package relative header file for the PPI. An optional comment following an entry
> may be used to provide simple information.

## 3.8 [Ppis] Sections


**Prototype**

```ini
<PpiEntries>          ::= [<PpiComment>]
~~                        <TS> <CName> <Eq> <CFormatGUID>~~
~~                        {<CommentBlock>} {<EOL>}~~
>                         <TS> <CName> <Eq> <GuidValue> [<CommentBlock>] <EOL>

> <GuidValue>         ::= {<CFormatGuid>} {<RegistryFormatGuid>}

<PpiComment>          ::= [<Description>]
>                         [<SinglePpi>]
                          <TS> "##" <TS> <PpiHdrFile> <EOL>

> <SinglePpi>         ::= <TS> "@SinglePpi" <EOL>
> 
<PpiHdrFile>          ::=  <PATH> <Word> ".h"
```

**Example**
```ini
#######################################################################
#
# Global Ppis Definition section - list of Global Ppis C Name
# Data Structures that are provided by this package.
#
#######################################################################
~~[Ppis.common]~~
~~gPeiNtThunkPpiGuid = { 0x98C281E5, 0xF906, 0x43DD, \~~
~~{ 0xA9, 0x2B, 0xB0, 0x03, 0xBF, 0x27, 0x65, 0xDA }}~~
~~gNtPeiLoadFilePpiGuid = { 0xFD0C65EB, 0x0405, 0x4CD2, \~~
~~{ 0x8A, 0xEE, 0xF4, 0x00, 0xEF, 0x13, 0xBA, 0xC2 }}~~
~~gNtFwhPpiGuid = { 0x4E76928F, 0x50AD, 0x4334, \~~
~~{ 0xB0, 0x6B, 0xA8, 0x42, 0x13, 0x10, 0x8A, 0x57 }}~~
~~gPeiNtAutoScanPpiGuid = { 0x0DCE384D, 0x007C, 0x4BA5, \~~
~~{ 0x94, 0xBD, 0x0F, 0x6E, 0xB6, 0x4D, 0x2A, 0xA9 }}~~

> [Ppis]
>   ## Include/Ppi/PostBootScriptTable.h
>   gPeiPostScriptTablePpiGuid    =  { 0x88c9d306, 0x900, 0x4eb5, \
>     { 0x82, 0x60, 0x3e, 0x2d, 0xbe, 0xda, 0x1f, 0x89}}
>     
>   ## Include/Ppi/SerialPortPei.h
>   # @SinglePpi
>   gPeiSerialPortPpiGuid         =  { 0x490e9d85, 0x8aef, 0x4193, \
>     { 0x8e, 0x56, 0xf7, 0x34, 0xa9, 0xff, 0xac, 0x8b}}
>     
>   ## Include/Ppi/UfsHostController.h
>   gEdkiiPeiUfsHostControllerPpiGuid  =  dc54b283-1a77-4cd6-83bb-fdda469a2ec6
>   

```

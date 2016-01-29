# Document Change Notice


Change Document: EDK II Package Declaration (DEC) File Specification

(http://github.com/tianocore-docs/Docs)

Current Document Revision: 1.25

Target Revision: 1.26

DCN Date: 27 Jan 2016

### Summary

1. Allow use of Registry Format GUID to declarations
2. Adding new reserved comment, ```@SingleGuid <GuidType>```


## 2.6 [Guids] Usage
This is an optional section.

This section is used to define the GUID Value for Guid C Names.

This section uses one of the following section definitions:

```[Guids] [Guids.IA32] [Guids.X64] [Guids.IPF] [Guids.EBC]
[Guids.common] [Guids.IA32, Guids.X64] [Guids.X64, Guids.IPF]```

Format for the entries in this section is two fields with an equal "```=```" character separating the fields as shown below.
```ini
> #Comment Block
~~GuidCName = {C Format Guid Value} # Comment~~
> GuidCName = Guid Value # Comment
```

~~The Comment section can be used to identify the list of supported module types.~~

> A comment block preceding the entry must be used to provide detailed  information, including the name of the package relative header file for the GUID. An optional comment following an entry may be used to provide simple information.


## 3.6 [Guids] Sections
**Prototype**
```ini
  <Guids>        ::= "[Guids" [<com_attribs>] "]" <EOL>
                      <GuidEntries>*
                      
  <com_attribs>    ::= {".common"} {<attribs>}
  
  <attribs>        ::= <attrs> ["," <TS> "Guids" <attrs>]*
  
  <attrs>          ::= "." <arch>
  
  <GuidEntries>    ::= [<GuidComment>]
~~                        <TS> <CName> <Eq> <CFormatGuid>~~
>                       <TS> <CName> <Eq> <GuidValue>
                        {<CommentBlock>} {<EOL>}
  
  <GuidComment>    ::= [<Description>]
>                      [<SingleGuid>]*
                        <TS> "##" <TS> <GuidHeaderFile> <EOL>

>  <SingleGuid>      ::= <TS> "#" <TS> "@SingleGuid" <GuidUseType> <EOL> 
>  <GuidUseType>     ::= <TS> ":" <TS> <GuidType>
>  <GuidType>        ::= {"Event"} {"File"} {"FV"} {"GUID"} {"HII"} {"HOB"}
>                        {"SystemTable"} {"TokenSpaceGuid"} {"Variable"}
>                        {"UNDEFINED"}
  
  ~~<GuidValue>      ::= <CFormatGUID>~~
>  <GuidValue>      ::= {<CFormatGUID>} {<RegistryFormatGUID>}
  
  <GuidHeaderFile> ::= <PATH> <Word> ".h"
  
  <Description>    ::= <TS> "##" <TS> <AsciiString> <EOL>
                       [<TS> "#" <TS> <AsciiString> <EOL>]*
  
  <CommentBlock>   ::= <TS> "##" <TS> <ModuleTypeList>
                       {<Comment>} {<EOL>}
 ```
 
 **Example**
 ```ini
#######################################################################
#
# Global Guid Definition section - list of Global Guid C Name
# Data Structures that are provided by
# this package.
#
#######################################################################
~~[Guids.common]
gPcdHobGuid = { 0x582E7CA1, 0x68CD, 0x4D44, \
{ 0xB4, 0x3B, 0xF2, 0x98, 0xED, 0x58, 0x7B, 0xA6 }}
gEfiWinNtPassThroughGuid = { 0xCC664EB8, 0x3C24, 0x4086, \
{ 0xB6, 0xF6, 0x34, 0xE8, 0x56, 0xBC, 0xE3, 0x6E }}
gEfiWinNtCPUSpeedGuid = { 0xD4F29055, 0xE1FB, 0x11D4, \
{ 0xBD, 0x0D, 0x00, 0x80, 0xC7, 0x3C, 0x88, 0x81 }}
gEfiWinNtCPUModelGuid = { 0xBEE9B6CE, 0x2F8A, 0x11D4, \
{ 0xBD, 0x0D, 0x00, 0x80, 0xC7, 0x3C, 0x88, 0x81 }}
gEfiWinNtMemoryGuid = { 0x99042912, 0x122A, 0x11D4, \
{ 0xBD, 0x0D, 0x00, 0x80, 0xC7, 0x3C, 0x88, 0x81 }}
gEfiWinNtConsoleGuid = { 0xBA73672C, 0xA5D3, 0x11D4, \
{ 0xBD, 0x00, 0x00, 0x80, 0xC7, 0x3C, 0x88, 0x81 }}
gEfiWinNtUgaGuid = { 0xAB248E99, 0xABE1, 0x11D4, \
{ 0xBD, 0x0D, 0x00, 0x80, 0xC7, 0x3C, 0x88, 0x81 }}
gEfiWinNtGopGuid = { 0x4e11e955, 0xccca, 0x11d4, \
{ 0xbd, 0x0d, 0x00, 0x80, 0xc7, 0x3c, 0x88, 0x81 }}
gEfiWinNtSerialPortGuid = { 0x0C95A93D, 0xA006, 0x11D4, \
{ 0xBC, 0xFA, 0x00, 0x80, 0xC7, 0x3C, 0x88, 0x81 }}
gEfiWinNtFileSystemGuid = { 0x0C95A935, 0xA006, 0x11D4, \
{ 0xBC, 0xFA, 0x00, 0x80, 0xC7, 0x3C, 0x88, 0x81 }}
gEfiWinNtPhysicalDisksGuid = { 0x0C95A92F, 0xA006, 0x11D4, \
{ 0xBC, 0xFA, 0x00, 0x80, 0xC7, 0x3C, 0x88, 0x81 }}
gEfiWinNtVirtualDisksGuid = { 0x0C95A928, 0xA006, 0x11D4, \
{ 0xBC, 0xFA, 0x00, 0x80, 0xC7, 0x3C, 0x88, 0x81 }}
gEfiEdkNt32PkgTokenSpaceGuid = { 0x0D79A645, 0x1D91, 0x40a6, \
{ 0xA8, 0x1F, 0x61, 0xE6, 0x98, 0x2B, 0x32, 0xB4 }}~~

>[Guids]
>  ## MdeModule package token space guid
>  # Include/Guid/MdeModulePkgTokenSpace.h
>  gEfiMdeModulePkgTokenSpaceGuid     = { 0xA1AFF049, 0xFDEB, \
>    0x442a, { 0xB3, 0x20, 0x13, 0xAB, 0x4C, 0xB7, 0x2B, 0xBC }}
>
>  ## Hob guid for Pcd DataBase
>  #  Include/Guid/PcdDataBaseHobGuid.h
>  gPcdDataBaseHobGuid                = { 0xEA296D92, 0x0B69, \
>    0x423C, { 0x8C, 0x28, 0x33, 0xB4, 0xE0, 0xA9, 0x12, 0x68 }}
>
>  ## Include/Guid/AcpiS3Context.h 
>  gEfiAcpiS3ContextGuid              = { 0xef98d3a, 0x3e33, \
>    0x497a, { 0xa4, 0x1, 0x77, 0xbe, 0x3e, 0xb7, 0x4f, 0x38 }}
>
>  ## Include/Guid/BootScriptExecutorVariable.h
>  # @SingleGuid : GUID
>  gEfiBootScriptExecutorVariableGuid = { 0x3079818c, 0x46d4, \
>    0x4a73, { 0xae, 0xf3, 0xe3, 0xe4, 0x6c, 0xf1, 0xee, 0xdb }}
>
>  ## Include/Guid/BootScriptExecutorVariable.h
>  # @SingleGuid : GUID
>  gEfiBootScriptExecutorContextGuid  = { 0x79cb58c4, 0xac51, \
>    0x442f, { 0xaf, 0xd7, 0x98, 0xe4, 0x7d, 0x2e, 0x99, 0x8 }}
> 
>  ## Include/Guid/Ip4Config2Hii.h
>  gIp4Config2NvDataGuid              = 9b942747-154e-4d29-a436-bf7100c8b53b

```
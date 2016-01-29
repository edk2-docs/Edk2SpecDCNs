# Document Change Notice

Change Document: EDK II Package Declaration (DEC) File Specification
(http://github.com/tianocore-docs/Docs)

Current Document Revision: 1.25
New Revision: 1.26

DCN Date: 27 Jan 2016

### Summary

1. Allow use of Registry Format GUID to declarations
2. Adding new reserved comment, ```@SingleProtocol```

## 2.7 [Protocols] Usage
This is an optional section.

This section is used to define the GUID Value for Protocol C Names.

This section uses one of the following section definitions:

```[Protocols] [Protocols.IA32] [Protocols.X64] [Protocols.IPF] [Protocols.EBC]
[Protocols.common] ```

Format for the entries in this section is two fields with an equal “```=```” character separating the fields as shown below.
```ini
> 
> \# Comment Block
>  ProtocolCName = Guid Value # Comment
~~ProtocolCName = {C Format Guid Value} # Comment~~
```
~~The Comment section can be used to identify the list of supported module types.~~

> A comment block preceding the entry must be used to provide detailed  information, including the
> name of the package relative header file for the Protocol. An optional comment following an entry
> may be used to provide simple information.


## 3.7 [Protocols] Sections


**Prototype***

```ini
<ProtocolEntries>   ::= [<ProtocolComment>]
~~                        <TS> <CName> <Eq> <CFormatGUID>~~
~~                        {<CommentBlock>} {<EOL>}~~
>                        <TS> <CName> <Eq> <GuidValue> [<CommentBlock>] <EOL>

> <GuidValue>         ::= {<CFormatGuid>} {<RegistryFormatGuid>}

<ProtocolComment>   ::= [<Description>]
>                       [<SingleProtocol>]
                        <ProtoHdrFile>

> <SingleProtocol>  ::= <TS> "@SingleProtocol" <EOL>
> 
<ProtoHdrFile>      ::= <TS> "##" <TS> <PATH> <Word> ".h"
```

**Example**

```ini
#######################################################################
#
# Global Protocols Definition section - list of Global Protocols C Name
# Data Structures that are provided by this package.
#
#######################################################################
[Protocols]
  ~~gEfiWinNtThunkProtocolGuid = { 0x58C518B1, 0x76F3, 0x11D4, \~~
    ~~{ 0xBC, 0xEA, 0x00, 0x80, 0xC7, 0x3C, 0x88, 0x81 }}~~
  ~~gEfiWinNtIoProtocolGuid = { 0x96EB4AD6, 0xA32A, 0x11D4, \~~
    ~~{ 0xBC, 0xFD, 0x00, 0x80, 0xC7, 0x3C, 0x88, 0x81 }}~~

>  ## Print protocol defines basic print functions to print the format unicode and 
>  # ascii string.
>  # Include/Protocol/Print2.h
>  gEfiPrint2ProtocolGuid          = { 0xf05976ef, 0x83f1, 0x4f3d, \
>    { 0x86, 0x19, 0xf7, 0x59, 0x5d, 0x41, 0xe5, 0x38 } }
>     
>  ## This protocol defines the generic memory test interfaces in Dxe phase.
>  # @SingleProtocol
>  # Include/Protocol/GenericMemoryTest.h
>  gEfiGenericMemTestProtocolGuid = { 0x309DE7F1, 0x7F5E, 0x4ACE, \
>    { 0xB4, 0x9C, 0x53, 0x1B, 0xE5, 0xAA, 0x95, 0xEF }}
>
>  ## Fault Tolerant Write protocol provides boot-time service to do fault tolerant write 
>  # capability for block devices.
>  # @SingleProtocol
>  #  Include/Protocol/FaultTolerantWrite.h
>  gEfiFaultTolerantWriteProtocolGuid = { 0x3EBD9E82, 0x2C78, 0x4DE6, \
>  { 0x97, 0x86, 0x8D, 0x4B, 0xFC, 0xB7, 0xC8, 0x81 }}
>  
>  ## This protocol provides boot-time service to do fault tolerant write capability for 
>  # block devices in SMM environment.
>  #  Include/Protocol/SmmFaultTolerantWrite.h
>  gEfiSmmFaultTolerantWriteProtocolGuid = 3868fc3b-7e45-43a7-906c-4ba47de1754d
>  

```

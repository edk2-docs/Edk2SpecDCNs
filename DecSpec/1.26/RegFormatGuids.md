# Document Change Notice

Change Document: EDK II Package Declaration (DEC) File Specification

(http://github.com/tianocore-docs/Docs)

Current Document Revision: 1.25

Target Revision: 1.26

DCN Date: 08 Feb 2016

### Summary

This DCN adds support for specifying GUID values as a Registry Format GUID as
well as a C Format GUID.


## 2.6 [Guids] Usage

This is an optional section.

This section is used to define the GUID Value for Guid C Names.

This section uses one of the following section definitions:
```ini
[Guids] [Guids.IA32] [Guids.X64] [Guids.IPF] [Guids.EBC]
[Guids.common] [Guids.IA32, Guids.X64] [Guids.X64, Guids.IPF]
```

Format for the entries in this section is two fields with an equal “=” 
character separating the fields as shown below.

~~```GuidCName = {C Format Guid Value} # Comment```~~
> ```GuidCName = <GuidValue> # Comment```

The Comment section can be used to identify the list of supported module types.

## 2.7 [Protocols] Usage

This is an optional section.

This section is used to define the GUID Value for Protocol C Names.

This section use ones of the following section definitions:

```ini
[Protocols] [Protocols.IA32] [Protocols.X64] [Protocols.IPF]
[Protocols.EBC] [Protocols.common]
```

Format for the entries in this section is two fields with an equal “=” 
character separating the fields as shown below.

~~```ProtocolCName = {C Format Guid Value} # Comment```~~
> ```ProtocolCName = <GuidValue> # Comment```

The Comment section can be used to identify the list of supported module types.

## 2.8 [Ppis] Usage

This is an optional section.

This section is used to define the GUID Value for PPI C Names.

This section use ones of the following section definitions:

```ini
[Ppis] [Ppis.IA32] [Ppis.X64] [Ppis.IPF] [Ppis.EBC] [Ppis.common]
```

Format for the entries in this section is two fields with an equal “=” 
character separating the fields as shown below.

~~```PpiCName = {C Format Guid Value} # Comment```~~
~~```PpiCname1 = RegistryFormatGUID # Comment```~~
> ```PpiCName = <GuidValue> # Comment```

The Comment section can be used to identify the list of supported module types.


## 3.6 [Guids] Sections

**Prototype**

```ini
<Guids>          ::= "[Guids" [<com_attribs>] "]" <EOL>
                     <GuidEntries>*

<com_attribs>    ::= {".common"} {<attribs>}

<attribs>        ::= <attrs> ["," <TS> "Guids" <attrs>]*

<attrs>          ::= "." <arch>

<GuidEntries>    ::= [<GuidComment>]
~~                     <TS> <CName> <Eq> <CFormatGUID> {<CommentBlock>} {<EOL>}~~
>                     <TS> <CName> <Eq> <GuidValue> {<CommentBlock>} {<EOL>}~~

<GuidComment>    ::= [<Description>]
                     <TS> "##" <TS> <GuidHeaderFile> <EOL>

~~<GuidValue>      ::= <CFormatGUID>~~
> <GuidValue>      ::= {<CFormatGUID>} {<RegFormatGUID>}

<GuidHeaderFile> ::= <PATH> <Word> ".h"

<Description>    ::= <TS> "##" <TS> <AsciiString> <EOL>
                     [<TS> "#" <TS> <AsciiString> <EOL>]*
                     
<CommentBlock>   ::= <TS> "##" <TS> <ModuleTypeList> {<Comment>} {<EOL>}
```

## 3.7 [Protocols] Sections

** Prototype**

```ini
<Protocols>       ::= "[Protocols" [<com_attribs>] "]" <EOL>
                      <ProtocolEntries>*

<com_attribs>     ::= {".common"} {<attribs>}

<attribs>         ::= <attrs> ["," <TS> "Protocols" <attrs>]8

<attrs>           ::= "." <arch>

<ProtocolEntries> ::= [<ProtocolComment>]
~~                      <TS> <CName> <Eq> <CFormatGUID> {<CommentBlock>} {<EOL>}~~
>                      <TS> <CName> <Eq> <GuidValue> {<CommentBlock>} {<EOL>}

<GuidValue>       ::= {<CFormatGUID>} 
<ProtocolComment> ::= [<Description>]
                      <ProtoHdrFile>

<ProtoHdrFile>    ::= <TS> "##" <TS> <PATH> <Word> ".h"

<Description>     ::= <TS> "##" <TS> <AsciiString> <EOL>
                      [<TS> "#" <TS> <AsciiString> <EOL>]*

<CommentBlock>    ::= [<TS> "##" <TS> <ModuleTypeList>] {<Comment>} {<EOL>}
```

## 3.8 [PPIs] Sections

**Prototype***

```ini
<Ppis>           ::= "[Ppis" [<com_attribs>] "]" <EOL>
                     <PpiEntries>*

<com_attribs>    ::= {".common"} {<attribs>}

<attribs>        ::= <attrs> ["," <TS> "Ppis" <attrs>]*

<attrs>          ::= "." <arch>

<PpiEntries>     ::= [<PpiComment>]
~~                     <TS> <CName> <Eq> <CFormatGUID>~~
>                     <TS> <CName> <Eq> <GuidValue>
                     {<CommentBlock>} {<EOL>}

<GuidValue>      ::= {<CFormatGuid>} {<RegFormatGuid>}

<PpiComment>     ::= [<Description>]
                     <TS> "##" <TS> <PpiHeaderFile> <EOL>

<Description>    ::= <TS> "##" <TS> <AsciiString> <EOL>
                     [<TS> "#" <TS> <AsciiString> <EOL>]*

<PpiHeaderFile>  ::= <PATH> <Word> ".h"

<CommentBlock>   ::= [<TS> "##" <TS> <ModuleTypeList
```

3.10 PCD Sections

**Prototype**

```ini

<PcdPtrVal> ::= <PtrVal> <FS> "VOID*"

~~<PtrVal>    ::= {<CString>} {<CArray>}~~
> <PtrVal>    ::= {<CString>} {<CArray>} {<GuidValue>}
> 
> <GuidValue> ::= {<CFormatGuid>} {<RegFormatGuid>}

<Token>     ::= <NumValUint32>
```




# Document Change Notice


Change Document: EDK II Package Declaration (DEC) File Specification
(http://github.com/tianocore-docs/Docs)

Current Document Revision: 1.25
New Revision: 1.26

DCN Date: 27 Jan 2016

### Summary

Add new syntax to the DEC file for specifying information that can only be used by modules within the package. When modules outside the packages attempt to use this content, the EDK II build system must break with an error regarding content not found.

The four sections, Includes, Ppis, Guids and Protocols headers will be modified with a keyword, Private following the architecture modifier. If Private is not present, then the content is usable by modules outside the package.

## 2.5 [Includes] Usage

Also included in this section are the directories containing headers that may be required for individual EDK II module types. Refer to Appendix, "*EDK II Module Types*", for a list of the valid types.

The section tag modifier, Private, is used to restrict the EDK II build system by preventing references to content in these sections from being used by modules outside of the package. It is not permissible to mix section tags without the Private attribute with section tags with the Private attribute.

For example, ```[Includes.common, Includes.IA32.Private]``` is prohibited.

Refer to the ```[Includes]``` definition later in this document for a complete description of this section and its contents.

The [Includes] section uses one of the following section definitions:
```ini
~~[Includes.common] [Includes.IA32] [Includes.X64] [Includes.IPF]~~
~~[includes.EBC] [Includes]~~
> [Includes.common] [Includes.common.Private] [Includes.IA32] 
> [Includes.IA32.Private] [Includes.X64] [Includes.X64.Private] 
> [Includes.IPF] [Includes.IPF.Private] [includes.EBC] 
> [includes.EBC.Private] [Includes]
```

## 2.6 [Guids] Usage
This is an optional section.

This section is used to define the GUID Value for Guid C Names.

> The section tag modifier, Private, is used to restrict the EDK II build system by preventing references to content in these sections from being used by modules outside of the package. It is not permissible to mix section tags without the Private attribute with section tags with the Private attribute.

This section use ones of the following section definitions:
```ini
~~[Guids] [Guids.IA32] [Guids.X64] [Guids.IPF]~~
~~[Guids.EBC] [Guids.common] [Guids.IA32, Guids.X64] [Guids.X64, Guids.IPF]~~

> [Guids] [Guids.common] [Guids.common.Private] [Guids.IA32]
> [Guids.IA32.Private] [Guids.X64] [Guids.X64.Private]
> [Guids.IPF] [Guids.IPF.Private] [Guids.EBC]
> [Guids.EBC.Private]
```
> Architectural sections may also be combined, as in:
```ini
> [Guids.IA32, Guids.X64]
> [Guids.IA32.Private, Guids.X64.Private]
```

## 2.7 [Protocols] Usage
This is an optional section.

This section is used to define the GUID Value for Protocol C Names.

> The section tag modifier, Private, is used to restrict the EDK II build system by preventing references to content in these sections from being used by modules outside of the package. It is not permissible to mix section tags without the Private attribute with section tags with the Private attribute.

This section use ones of the following section definitions:
```ini
~~[Protocols] [Protocols.IA32] [Protocols.X64] [Protocols.IPF]~~
~~[Protocols.EBC] [Protocols.common]~~

> [Protocols] [Protocols.common] [Protocols.common.Private] [Protocols.IA32]
> [Protocols.IA32.Private] [Protocols.X64] [Protocols.X64.Private]
> [Protocols.IPF] [Protocols.IPF.Private] [Protocols.EBC]
> [Protocols.EBC.Private]

```

> Architectural sections may also be combined, as in:
```ini
> [Protocols.IA32, Protocols.X64]
> [Protocols.IA32.Private, Protocols.X64.Private]
```

## 2.8 [Ppis] Usage
This is an optional section.

This section is used to define the GUID Value for PPI C Names.

> The section tag modifier, Private, is used to restrict the EDK II build system by preventing references to content in these sections from being used by modules outside of the package. It is not permissible to mix section tags without the Private attribute with section tags with the Private attribute.

This section use ones of the following section definitions:
```ini
~~[Ppis] [Ppis.IA32] [Ppis.X64] [Ppis.IPF] [Ppis.EBC] [Ppis.common]~~
> [Ppis] [Ppis.common] [Ppis.common.Private] [Ppis.IA32] [Ppis.IA32.Private]
> [Ppis.X64] [Ppis.X64.Private] [Ppis.IPF] [Ppis.IPF.Private] [Ppis.EBC]
> [Ppis.EBC.Private]

```

> Architectural sections may also be combined, as in:
```ini
> [Ppis.IA32, Ppis.X64]
> [Ppis.IA32.Private, Ppis.X64.Private]
```

## 3.5 [Includes] Sections

**Prototype**

```ini
<Include>      ::= "[Includes" [<com_attribs>] "]" <EOL>
                   <IncEntries>*

~~ <com_attribs>  ::= {".common"} {<attribs>}~~
> <com_attribs>  ::= {<Public>} {<Hidden>}

> <Public>       ::= {".common"} {<attribs>}
> 
> <Hidden>       ::= {".common.Private"} {<hattribs>}
> 
<attribs>      ::= <attrs> ["," <TS> "Includes" <attrs>]*

> <hattribs>     ::= <hattrs> ["," <TS> "includes" <hattrs>]*
> 
<attrs>        ::= "." <arch>
>  
> <hattrs>        ::= "." <arch> ".Private"

```

## 3.6 [Guids] Sections

**Prototype***
```ini
<Guids>         ::= "[Guids" [<com_attribs>] "]" <EOL>
                    <GuidEntries>*
                    
~~<com_attribs>   ::= {".common"} {<attribs>}~~
> <com_attribs>   ::= {<Public>} {<Hidden>}
>
> <Public>        ::= {".common"} {<attribs>}
>
> <Hidden>       ::= {".common.Private"} {<hattribs>}
 
<attribs>       ::= <attrs> ["," <TS> "Guids" <attrs>]*

<attrs>         ::= "." <arch>
> 
> <hattribs>     ::= <hattrs> ["," <TS> "Guids" <hattrs>]*
>
> <hattrs>        ::= "." <arch> ".Private"

```

## 3.7 [PPIs] Sections

**Prototype***
```ini
<Ppis>          ::= "[Ppis" [<com_attribs>] "]" <EOL>
                    <PpiEntries>*
                    
~~<com_attribs>   ::= {".common"} {<attribs>}~~
> <com_attribs>   ::= {<Public>} {<Hidden>}
>
> <Public>        ::= {".common"} {<attribs>}
>
> <Hidden>       ::= {".common.Private"} {<hattribs>}
 
<attribs>       ::= <attrs> ["," <TS> "Ppis" <attrs>]*

<attrs>         ::= "." <arch>
> 
> <hattribs>     ::= <hattrs> ["," <TS> "Ppis" <hattrs>]*
>
> <hattrs>        ::= "." <arch> ".Private"

```

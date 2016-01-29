# Document Change Notice


Change Document: EDK II Flash Definition (FDF) File Specification

(http://github.com/tianocore-docs/Docs)

Current Document Revision: 1.26

Target Revision: 1.27

DCN Date: 27 Jan 2016


### Summary

1. Extend the FILE RAW statement format to support multiple binary files.


## 3.6 [FV] Sections

**Prototype**

```ini
<type3>     ::= <TS> "FILE" <MTS> "RAW" <Eq> <NamedGuidOrPcd>
                <Options2>

...

<Options2>  ::= [<Use>] [<FileOpts>] <MTS>
                "{" [<EOL>]
~~                    {<Filename>} {<SectionData>} <TS>~~
~~                "}" [<EOL>]~~
>                   <TS> {<Filename>} {<FileList>+} {<SectionData> <EOL>}
                "}" <EOL>
>
> <FileList> ::= [<FfsAlignment>] <NormalFile> <EOL>

...

~~<Filename> ::= {<FvImage>} {<FdImage>} {<NormalFile>}~~
> <Filename> ::= {<FvImage>} {<FdImage>} {<NormalFile>} <EOL>

```

**Examples**

**Append the following at the end of the Example in 3.6***

> ```ini
FILE RAW = 197DB236-F856-4924-90F8-CDF12FB975F3 {
$(OUTPUT_DIRECTORY)/$(TARGET)_$(TOOL_CHAIN_TAG)/$PLATFORM_ARCH)/File.bin
}
```
> ```ini
FILE RAW = 197DB236-F856-4924-90F8-CDF12FB975F3 {
  Align=16 $(PLATFORM_PACKAGE)/Binaries/File1.pdb
  Align=16 $(PLATFORM_PACKAGE)/Binaries/File1.pdb
  Align=16 $(PLATFORM_PACKAGE)/Binaries/File1.pdb
}
```


## 3.7 [Capsule] Sections

**Prototype**

```ini
<type3>     ::= <TS> "FILE" <MTS> "RAW" <Eq> <NamedGuidOrPcd>
                <Options2>

...

<Options2>  ::= [<Use>] [<FileOpts>] <MTS>
                "{" [<EOL>]
~~                   <TS> {<Filename>} {<SectionData>} <TS>~~
>                   <TS> {<Filename>} {<FileList>} {<SectionData> <EOL>}
                "}" [<EOL>]
>
> <FileList> ::= [<FfsAlignment>] <NormalFile>

...

~~<Filename>   ::= {<FvImage>} {<FdImage>} {<NormalFile>}~~
> <Filename>   ::= {<FvImage>} {<FdImage>} {<NormalFile>} <EOL>

```
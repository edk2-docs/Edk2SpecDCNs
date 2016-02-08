# Document Change Notice

Change Document: EDK II Module Information (INF) File Specification

(http://github.com/tianocore-docs/Docs)

Current Document Revision: 1.25

Target Revision: 1.26

DCN Date: 08 Feb 2016

### Summary

This DCN adds support for specifying VOID* PCD values as a Registry Format GUID as well as a C Format GUID.

## 3.8 PCD Sections

**Prototype**

```ini
<Value>        ::= if (pcddatumtype == "BOOLEAN"):
                     <Boolean>
                   elif (pcddatumtype == "UINT8"):
                     <NumValUint8>
                   elif (pcddatumtype == "UINT16"):
                     <NumValUint16>
                   elif (pcddatumtype == "UINT32"):
                     <NumValUint32>
                   elif (pcddatumtype == "UINT64"):
                     <NumValUint64>
                   else:
                     <StringVal>

~~<stringVal>  ::= {<StringType>} {<CArray>}~~
> <stringVal>  ::= {<StringType>} {<CArray>} {<GuidValue>}
> 
> <GuidValue>  ::= {<CFormatGuid>} {<RegFormatGuid>}

<StringType>   ::= {<UnicodeString>} {<CString>}

<FFE>          ::= <FS> <FeatureFlagExpress>
```

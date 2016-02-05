# Document Change Notice


Change Document: EDK II Build Specification

(http://github.com/tianocore-docs/Docs)

Current Document Revision: 1.26

Target Revision: 1.27

DCN Date: 5 Feb 2016

### Summary

FDF spec will allow specifying multiple binaries in the ```FILE RAW``` statements in FV and Capsule sections.

### 10.3.2 Creating EFI Sections
**Append the following at the end of this section**

```FILE``` statements in the FDF file's ```[FV]``` or ```[Capsule]``` sections are provided so that a platform integrator can include complete EFI FFS files, as well as a method for constructing FFS files using curly "{}" brace scoping.

FFS file specification syntax is one of the following:
```ini
FILE Type $(NAMED_GUID) [Options] FileName
```
OR
```ini
FILE Type $(NAMED_GUID) [Options] {
SECTION SECTION_TYPE = FileName
SECTION SECTION_TYPE = FileName
} 
```
When constructing a ```RAW``` type, (```EFI_FV_FILETYPE_RAW```) FFS file, the content is parsed and if multiple binary files are listed, they will be merged into a single binary file. Each file is appended sequentially in the order listed in the FDF file. If an Align value is specified, padding values of 0 may be inserted prior to appending the file to ensure correct address alignment. If no alignment value is specified, the files no padding is performed (byte alignment). If the alignment value is ```Auto```, then each file will start on an architectural natural boundary.

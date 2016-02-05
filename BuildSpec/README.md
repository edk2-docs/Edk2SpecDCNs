# DCNs for the EDK II Build Specification

(http://github.com/tianocore-docs/Docs)

**Target Revision: 1.27**

**Target Release Date: February 26, 2016**

## Revision History

- *Revision number must change when there is a change to the specification that includes new content.*
- *Changes considered bug fixes to the specification may use the same revision number, with an Errata tag. Errata tags are alpha characters.*


| Revision Number  | Description  | Date   |
| :--: | :--- | ---: |
| 1.26 | Updates:  | January 2016 |
|   | - Specification revision to 1.26 | |
|   | - Removed data structure definitions (duplicates from PE/COFF, PI Specifications and TE headers) in Chapter 3 and included references to the industry specifications to remove potential typographical errors and inconsistencies. |   |
|   | - Removed Setup and Getting Started sections from Quick Start chapter 6 - this information is available on the TianoCore.org web-site. |   |
|   | - Revised WORKSPACE wording for updated build system that can handle packages located outside of the WORKSPACE directory tree (refer to the TianoCore.org/EDKII website for additional instructions on setting up a development environment). Added new, optional system environment variables used by the build system in this environment. |  |
|   | - Provide clarification on VPD data generation and report for VPD data content |   |
|   | - Clarify precedence of the DPX_SOURCE and [Depex] section. |   |
|   | - Specify the alignment required for VOID* PCDs based on the string, Unicode string or byte-code array values. |   |
|   | - Remove Unicode file storage requirement; refer to the Multi-String UNI File Format Specification instead. |   |
|   | - Clarify BUILDRULEORDER |   |
|   | - Add support for INF statement in an FD region. |   |
| *1.27* | *Updates:* | *Target Date* |
|   | *- Specification revision to 1.27* |  |
|   | *- Allow Registry Format GUID values as well a C Format GUID values*  |   |
|   | *- Specify Private Content only used by modules within a package*     |   |
|   | *- Add new sub-section to the Build Report to show PCDs that are used in conditional directive statements in the DSC and FDF files that are not used in code by modules.* |  | 
|   | *- Add new sub-section to the Build Report to show MACROS that are used in conditional directive statemens in the DSC and FDF files.* |   |
|   |   |   |


[Individual DCNs](SUMMARY.md)
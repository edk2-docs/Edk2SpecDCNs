# Document Change Notice


Change Document: EDK II Platform Description (DSC) File Specification

(http://github.com/tianocore-docs/Docs)

Current Document Revision: 1.26

Target Revision: 1.27

DCN Date: 27 Feb 2016

### Summary

Process new syntax in the DEC file that specifys information that can only be used by modules within the package. When modules outside the packages attempt to use this content, the EDK II build system must break with an error regarding content not found.

The four sections, Includes, Ppis, Guids and Protocols headers will be the keyword, Private, following the architecture modifier. If Private is not present, then the content is usable by modules outside the package.
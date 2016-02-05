# Document Change Notice


Change Document: EDK II Platform Description (DSC) File Specification

(http://github.com/tianocore-docs/Docs)

Current Document Revision: 1.26

Target Revision: 1.27

DCN Date: 5 Feb 2016

### Summary

Update PCD processing to specify that a PCD's value may be set on the command-line, using the option:
```ini
--pcd <TokenSpaceGuidCname>.<PcdCName>=<Value>
```
A value on the command-line has the highest precedence. It will override all instances of the PCD's value specified in the DSC or FDF file.

# Document Change Notice

Change Document: EDK II Platform Description (DSC) File Specification

(http://github.com/tianocore-docs/Docs)

Current Document Revision: 1.26

Target Revision: 1.27

DCN Date: 23 Feb 2016

### Summary

Update the Report to include:
* Listing of PCDs that are used in conditional directives in the DSC and FDF files that are not used in module code.
* Update PCD keys to show command-line option override of values


---

### 13.3.1 Layout
The layout of the text report file:
```ini
|---- Platform summary
```
>```ini
    |----- Conditional directives section
```

```ini
    |----- Global PCD section
    |----- FD section*
        |---- FD Region sub-section*
        |---- VPD PCD Data sub-section*
    |---- Module section*
        |---- Basic Information summary
        |---- PCD sub-section
        |---- Library sub-section
        |---- DEPEX sub-section
        |---- Build_flags sub-section
        |---- Notification sub-section
```

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
    |----- Unused PCDs section
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

## 13.4 Platform Summary

Platform summary displays at the beginning of the output report, including the
following items:

* Platform Name : %Platform UI name: 'PLATFORM_NAME' in DSC [Defines] section%
* Platform DSC Path: %Path of platform DSC file%
* Architectures : %List string of all architectures used in build%
* Tool Chain : %Tool chain string%
* Target : %Target String"
* Output Path : %Path to platform build directory%
* Build Environment : %Environment string reported by Python%
* Build Duration : %Build duration time string%
* Report Content : %List of flags the control the report content%

>If the DSC or FDF file contains conditional directive statements (```!if, !elseif, !ifdef``` or ```!ifndef```) or the value of PCD is not used by a module is set in the DSC file (PCD Sections) or the FDF file (SET statements for example), the following sub-section may appear.

>The sub-section title will start with the following:

> ```ini
>==========================================================================<
Conditional Directives used by the build system
============================================================================
```

> If the DSC or FDF file define values for PCDs that are not used by any module and are not used in conditional directive statements, the following sub-section may appear.

> ```ini
>==========================================================================<
PCDs not used by modules or in conditional directives
============================================================================
```



> ### 13.4.1 PCDs in Conditional Directives

> If a PCD is used in a conditional directive statement, the PCD section will be displayed.

> PCD values derived from expressions or other PCDs are not differentiated in the report. Only the final value is displayed.

> The first line is required:

>```[*P|*F|*B] <PcdCName>: <PcdType> (<DatumType>) = <PcdValue>```
>   * ```*P``` means the Pcd's value was obtained from the DSC file
>   * ```*F``` means the PCD's value was obtained from the FDF file.
>   * ```*B``` means the PCD's value set by a build option.

> Additional lines may be displayed showing default values when the value is not a default value.

> **Example**

```ini
> >==========================================================================<
> Conditional Directives used by the build system
> ============================================================================
> PCD statements
> >--------------------------------------------------------------------------<
> gMyTokenSpaceGuid
> *P SmmEnable                   : FEATURE (BOOLEAN) = 0x0
>                                          DEC DEFAULT = 0x1
> *B LogEnable                   : FIXED   (UNIT32) = 0x1
>                                          DEC DEFAULT = 0x0
> <-------------------------------------------------------------------------->
> >==========================================================================<

```

> ### 13.4.2 PCDs not used

> If a PCD is not used in a conditional directive statement or by a module, the not used PCD section will be displayed.

> PCD values derived from expressions or other PCDs are not differentiated in the report. Only the final value is displayed.

> The first line is required:

>```[*P|*F|*B] <PcdCName>: <PcdType> (<DatumType>) = <PcdValue>```
>   * ```*P``` means the Pcd's value was obtained from the DSC file
>   * ```*F``` means the PCD's value was obtained from the FDF file.
>   * ```*B``` means the PCD's value set by a build option.

> Additional lines may be displayed showing default values when the value is not a default value.

> **Example**

```ini
> >==========================================================================<
> PCDs not used by modules or in conditional directives
> ============================================================================
> PCD statements
> >--------------------------------------------------------------------------<
> gMyTokenSpaceGuid
> *P SmmEnable                   : FEATURE (BOOLEAN) = 0x0
>                                          DEC DEFAULT = 0x1
> *B UsbEnable                   : FIXED   (UNIT32) = 0x1
>                                          DEC DEFAULT = 0x0
> <-------------------------------------------------------------------------->
> >==========================================================================<

```




## 13.5 Global PCD Section

This section contains the information for all PCDs whose values are the same for all
modules in a platform. The content of global PCD sub-section is grouped by token
space:

```ini
gEfiNt32PkgTokenSpaceGuid
…
…
gEfiMdeModulePkgTokenSpaceGuid
…
…
…
```

> PCD values derived from expressions or other PCDs are not differentiated in the report. Only the final value is displayed.

Each global PCD item contains one or more lines:

### 13.5.1 Required line
The first line is required:

~~```[*P|*F| ] <PcdCName>: <PcdType> (<DatumType>) = <PcdValue>```~~
>```[*P|*F|*B] <PcdCName>: <PcdType> (<DatumType>) = <PcdValue>```

* ```*P``` means the Pcd's value was obtained from the DSC file
* ```*F``` means the PCD's value was obtained from the FDF file.
* ```*B``` means the PCD's value was obtained from a build option.
* ~~If no ```*P``` or ```*F``` is given, the PCD's value comes from DEC file. If the value obtained from either the DSC or FDF is the same as the value in the DEC, then neither ```*P``` nor ```*F``` will be shown in the report.~~
* >If no ```*P```, ```*F``` or ```*B``` is shown, the PCD's value comes from DEC file. If the value obtained from either a build option, the DSC or FDF is the same as the value in the DEC, then ```*B```, ```*P``` or ```*F``` will not be shown in the report.

**Examples:**

```ini
*P PcdWinNtFirmwareVolume               : FIXED (VOID*) = L"..\\Fv\\Nt32.fd"
*F PcdWinNtFlashNvStorageFtwWorkingBase : FIXED (UINT32) = 0x0028E000
                                                DEC DEFAULT = 0x0

> gTokenSpaceGuid
> *B LogEnable                          : FIXED (UNIT32) = 0x1
>                                               DEC DEFAULT = 0x0

```

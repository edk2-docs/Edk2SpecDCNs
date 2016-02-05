# Document Change Notice


Change Document: EDK II Platform Description (DSC) File Specification

(http://github.com/tianocore-docs/Docs)

Current Document Revision: 1.26

Target Revision: 1.27

DCN Date: 27 Feb 2016

### Summary

Update the Report to include:
* Listing of PCDs that are used in conditional directives in the DSC and FDF files that are not used in module code.
* Listing of MACROs that are used in conditional directives in the DSC and FDF files.
* Update PCD keys to show command-line option override of values
* Display a SHA1 HASH of the .efi file in the Module's Summary Section if the ```-Y HASH``` option is present



---




## 13.1 Build Report Generation

***Add new item at the end of the defintions, before the Note ***

|  |   |
| ---: | :--- |
| > *Module Information*| |
|  | > Details of the module, may include the HASH of the .efi file.|


## 13.2 Sample Launch Steps: NT32 Platform

** starting with step 5b:**
5. Run "build.exe -a IA32 -p Nt32Pkg\Nt32Pkg.dsc -y ReportFile.txt"

    a) **-y**: This option specifies the output file name for build report.
    
    ~~b -Y: This option specifies flags that control the type of build report. It must be from the set of ```PCD, LIBRARY, DEPEX, BUILD_FLAGS, FLASH, FIXED_ADDRESS ```and ```EXECUTION_ORDER```. To specify more than one flag, repeat the option on the command line. Example of usage:~~
    >b)	**-Y**: This option specifies flags that control the type of build report. It must be from the set of ```PCD, LIBRARY, DEPEX, HASH, BUILD_FLAGS, FLASH, FIXED_ADDRESS``` and ```EXECUTION_ORDER```. To specify more than one flag, repeat the option on the command line. Example of usage:
On the command line, append the following arguments:

```"-y report_filename.txt -Y PCD -Y FLASH -Y DEPEX"```

~~The default set of flags (if **-Y** is not specified) is: ```PCD, LIBRARY, FLASH, DEPEX, BUILD_FLAGS``` and ```FIXED_ADDRESS```.~~


>The default set of flags (if **-Y** is not specified) is: ```PCD, LIBRARY, FLASH, DEPEX, HASH, BUILD_FLAGS ```and ```FIXED_ADDRESS```.

### 13.3.2 Section and Sub-section Format

**Example**
```ini
Platform Name: NT32
Platform DSC Path: s:\edk2\Nt32Pkg\Nt32Pkg.dsc
Architectures: IA32
Tool Chain: VS2008x86
Target: DEBUG
Output Path: s:\edk2\Build\NT32IA32
Build Environment: Windows-7-6.1.7601-SP1
Build Duration: 00:01:53
~~Report Contents: PCD, LIBRARY, BUILD_FLAGS, DEPEX, FLASH, FIXED_ADDRESS~~
```
> ```ini
Report Contents: PCD, LIBRARY, HASH, BUILD_FLAGS, DEPEX, FLASH, FIXED_ADDRESS
```

```ini
>==========================================================================<
Firmware Device (FD)
FD Name: NT32
Base Address: 0x0
Size: 0x2A0000(2688KB)
============================================================================
>--------------------------------------------------------------------------<
FD Region
Type: FV
Base Address: 0x0
Size: 0x280000 (2560K)
FV Name: FvRecovery (65.9% Full)
Occupied Size: 0x1A6028 (1688K)
Free Size: 0xD9FD8 (872K)
Offset Module
----------------------------------------------------------------------------
..(List of Module in FvRecovery)
<-------------------------------------------------------------------------->
>--------------------------------------------------------------------------<
..(List of other FD region sub-section)
>==========================================================================<
```

## 13.5 Global PCD Section

### 13.5.1 Required line
The first line is required:

~~```[*P|*F| ] <PcdCName>: <PcdType> (<DatumType>) = <PcdValue>```~~
>```[*P|*F|*B] <PcdCName>: <PcdType> (<DatumType>) = <PcdValue>```

* ```*P``` means the Pcd's value was obtained from the DSC file
* ```*F``` means the PCD's value was obtained from the FDF file.
* ```*B``` means the PCD's value was overridden by a command-line option.
* ~~If no ```*P``` or ```*F``` is given, the PCD's value comes from DEC file. If the value obtained from either the DSC or FDF is the same as the value in the DEC, then neither ```*P``` nor ```*F``` will be shown in the report.~~
* >If no ```*P```, ```*F``` or ```*B``` is shown, the PCD's value comes from DEC file. If the value obtained from either the DSC or FDF is the same as the value in the DEC, then neither ```*P``` nor ```*F``` will be shown in the report.

**Examples:**
```ini
*P PcdWinNtFirmwareVolume               : FIXED (VOID*) = L"..\\Fv\\Nt32.fd"
*F PcdWinNtFlashNvStorageFtwWorkingBase : FIXED (UINT32) = 0x0028E000
                                                DEC DEFAULT = 0x0
> *B gTokenSpaceGuid.LogEnable            : FIXED (UNIT32) = 0x1
>                                                 DEC DEFAULT = 0x0
>                                                 COMMAND LINE = TRUE

```

### 13.7.1 Module Section Summary

The following Entries are options:
> * If using defaults or the HASH flag is specified:
>   * SHA1 HASH:  %SHA1 HASH% and *%Module .efi file name%

* UEFI Specification Version: %The UEFI specification
version:'UEFI_SPECIFICATION_VERSION' in INF [Defines] section%
* PI Specification Version: %The PI specification version:'PI_SPECIFICATION_VERSION'
in the INF [Defines] section%
* PCI Device ID: %The PCI device ID for the device: 'PCI_DEVICE_ID' in INF [Defines]
section%

***Update Examples***

**Example1:**
```ini
>==========================================================================<
Module Summary
Module Name:         SmbiosDxe
Module INF Path:     MdeModule\Universal\SmbiosDxe\SmbiosDxe.inf
File GUID:           F9D88642-0737-49BC-81B5-6889CD57D9EA
Size:                0x7000 (28.00K)

> SHA1 HASH:           d94c3f180f25d6b562f477bc4a16b286cb66a8b6 *SmbiosDxe.efi

Build Time Stamp:    1969-12-31 16:00:00
Driver Type:         0x7 (DRIVER)
============================================================================
... (Module Section Details for SmbiosDxe)
<==========================================================================>
```

**Example2:**
```ini
>==========================================================================<
Module Summary
Module Name:         EbcDxe
Module INF Path:     MdeModule\Universal\EbcDxe\EbcDxe.inf
File GUID:           13AC6DD0-73D0-11D4-B06B-00AA00BD6DE7
Size:                0x9000 (36.00K)

> SHA1 HASH:           ff4c019345614afe5c88e7fc37219c30a07f4af4 *EbcDxe.efi

Time Stamp:          1969-12-31 16:00:00
Driver Type:         0x7 (DRIVER)
============================================================================
... (Module Section Details for EbcDxe)
<==========================================================================>
```

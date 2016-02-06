# Document Change Notice

Change Document: EDK II Platform Description (DSC) File Specification

(http://github.com/tianocore-docs/Docs)

Current Document Revision: 1.26

Target Revision: 1.28

DCN Date: 5 Feb 2016

### Summary

Update the Report to include:
* Listing of MACROs that are used in conditional directives in the DSC and FDF files that are not used in module code.



---



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

~~If the DSC or FDF file contained conditional directive statements (```!if, !elseif, !ifdef``` or ```!ifndef```), the following two sub-sections may appear. If a PCD is used in a conditional directive statement, the PCD section will be displayed.~~

>If the DSC or FDF file contained conditional directive statements (```!if, !elseif, !ifdef``` or ```!ifndef```), the following two sub-sections may appear. If a PCD is used in a conditional directive statement, the PCD section will be displayed. If a MACRO is used in a conditional directive statement, the MACRO section will be displayed.

> ### 13.4.2 MACROs

> If a PCD is used in a conditional directive statement, the PCD section will be displayed.

> The first line is required:

>```[*P|*F|*B] <MACRONAME>    : <Value> (line_no [: filename])```
>   * ```*P``` means the MACRO value was obtained from the DSC file
>   * ```*F``` means the MACRO value was obtained from the FDF file.
>   * ```*B``` means the MACRO was defined, or the value set using a command-line option.

> The line number is the number where the Macro was set in the DSC (```*P```) or FDF (```*P```) file. If the value was set in a file that was include (!include Filename) in the DSC or FDF, then the filename will be added after a colon character separator.

> **Example**
> ```ini
>==========================================================================<
Conditional Directives used by the build system
============================================================================
Macros used in !if and/or !elseif statements
>--------------------------------------------------------------------------<
*P X64_CONFIG                  : FALSE
                                 COMMAND LINE = /D X64_CONFIG=FALSE
*P ACPI50_ENABLE               : TRUE (50)
*P PERFORMANCE_ENABLE          : TRUE (54 : PlatformPkgConfig.dsc)
                                 COMMAND LINE = /D PERFORMANCE_ENABLE=TRUE
*P LFMA_ENABLE                 : FALSE (57 : PlatformPkgConfig.dsc)
*B MINNOW2_FSP_BUILD           : TRUE (24)
<-------------------------------------------------------------------------->
Macros used in !ifdef and/or !ifndef statements
>--------------------------------------------------------------------------<
*P ENABLE_USB                  : UNDEFINED
*P ENABLE_SEC                  : DEFINED
                                 COMMAND LINE /D ENABLE_SEC
<-------------------------------------------------------------------------->
```


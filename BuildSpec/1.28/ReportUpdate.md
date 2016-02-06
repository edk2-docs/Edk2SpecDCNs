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


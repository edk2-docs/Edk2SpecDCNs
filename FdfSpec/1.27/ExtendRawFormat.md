DCN


### Summary

1. Extend the RAW format to support multiple binary files.



**Examples**

> ```ini
FILE RAW = 197DB236-F856-4924-90F8-CDF12FB975F3 {
$(OUTPUT_DIRECTORY)/$(TARGET)_$(TOOL_CHAIN_TAG)/$PLATFORM_ARCH)/File.bin
}
```
> ```ini
FILE RAW = 197DB236-F856-4924-90F8-CDF12FB975F3 {
  Align=16 $(PLATFORM_PACKAGE)/Binaries/File1.pdb
  Align=16 $(PLATFORM_PACKAGE)/Binaries/File1.pdb
  Align=16 $(PLATFORM_PACKAGE)/Binaries/File1.pdb
}
```


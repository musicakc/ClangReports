# Analysis Report #

## General ##
**Warning Type:** Documentation   
**Warning Explanation:**:./include/linux/rhashtable.h:702:11: warning: parameter ':' not found in the function declaration [-Wdocumentation]
 * @params:     hash table parameters
          ^
**File Location:** include/linux/rhashtable.h
## History ##
**Introduced By:** ca26893f05e86 ("rhashtable: Add rhlist interface")  
**Reported Since:** TODO  
**Resolved By:** TODO

## Manuel Assesment ##
**Classification:** [Tool can detect during compiletime](WarningTypeClassifications.md)
### Rationale ###
This warning seems to be one that occurs very often but seems best to ignore it because it doesn't seem to indicate a real problem. The warning is for the documents indicating that the documented parameter names do not match the actual names of function parameters. So it seems like a false positive.

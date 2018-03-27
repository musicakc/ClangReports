# Analysis Report #

## General ##
**Warning Type:** Runtime: Duplicate Enum   
**Warning Explanation:**:In file included from ./include/linux/netfilter/nf_conntrack_common.h:5:
./include/uapi/linux/netfilter/nf_conntrack_common.h:20:2: warning: element IP_CT_IS_REPLY has been implicitly assigned 3 which another element has been assigned [-Wduplicate-enum]
        IP_CT_IS_REPLY,
        ^~~~~~~~~~~~~~
./include/uapi/linux/netfilter/nf_conntrack_common.h:22:2: note: element IP_CT_ESTABLISHED_REPLY also has value 3
        IP_CT_ESTABLISHED_REPLY = IP_CT_ESTABLISHED + IP_CT_IS_REPLY,
        ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**File Location:** include/uapi/linux/netfilter/nf_conntrack_common.h
## History ##
**Introduced By:** 94d0ec58e6315 ("UAPI: (Scripted) Disintegrate include/linux/netfilter")  
**Reported Since:** TODO  
**Resolved By:** TODO

## Manuel Assesment ##
**Classification:** [Tool can detect during runtime](WarningTypeClassifications.md)
### Rationale ###
During runtime, the duplicate enum value will cause the compiler to throw an exception. THe warning thus seems justified and requires the enum values to be checked to avoid duplicates. 

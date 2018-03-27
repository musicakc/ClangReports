# Analysis Report #

## General ##
**Warning Type:** Compiletime: Stack Frame Size   
**Warning Explanation:**:arch/x86/kvm/x86.c:7049:12: warning: stack frame size of 2136 bytes in function 'vcpu_enter_guest' [-Wframe-larger-than=]
static int vcpu_enter_guest(struct kvm_vcpu *vcpu)
           ^

**File Location:** arch/x86/kvm/x86.c
## History ##
**Introduced By:** 6de4f3ada40b3 ("KVM: Don't pass kvm_run arguments")  
**Reported Since:** TODO  
**Resolved By:** TODO

## Manuel Assesment ##
**Classification:** [Tool can detect during compile time](WarningTypeClassifications.md)
### Rationale ###
The warning seems to be generated in case larger stack frames are required which can be rectified by increasing the default value to avoid the warning.	


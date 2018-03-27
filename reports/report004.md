# Analysis Report #

## General ##
**Warning Type:** Compiletime: Enum Conversion   
**Warning Explanation:**:arch/x86/kvm/kvm_cache_regs.h:44:32: warning: implicit conversion from enumeration type 'enum kvm_reg_ex' to different enumeration type 'enum kvm_reg' [-Wenum-conversion]
                kvm_x86_ops->cache_reg(vcpu, VCPU_EXREG_PDPTR);
                ~~~~~~~~~~~                  ^~~~~~~~~~~~~~~~

**File Location:** arch/x86/kvm/kvm_cache_regs.h
## History ##
**Introduced By:** 6de4f3ada40b3 ("KVM: Cache pdptrs")  
**Reported Since:** https://lkml.org/lkml/2018/2/26/1151  
**Resolved By:** TODO

## Manuel Assesment ##
**Classification:** [Tool can detect during compile time](WarningTypeClassifications.md)
### Rationale ###
A patch has already been submitted for [this](https://lkml.org/lkml/2018/2/26/1151) warning. The implicit conversion warning can be removed by explicitly casting 'enum kvm_reg'.
	


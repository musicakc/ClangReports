# Analysis Report #

## General ##
**Warning Type:** Runtime: Constant Conversion   
**Warning Explanation:**:arch/x86/kvm/mmu.c:4281:39: warning: implicit conversion from 'int' to 'u8' (aka 'unsigned char') changes value from -171 to 85 [-Wconstant-conversion]
                u8 ff = (pfec & PFERR_FETCH_MASK) ? ~x : 0;
                   ~~                               ^~

**File Location:** arch/x86/kvm/mmu.c
## History ##
**Introduced By:** 09f037aa48f34 ("KVM: MMU: speedup update_permission_bitmask")  
**Reported Since:** TODO  
**Resolved By:** TODO

## Manuel Assesment ##
**Classification:** [Tool can detect during compile time](WarningTypeClassifications.md)
### Rationale ###
The implicit coversion for int to u8 gives a justified warning because a u8(unsigned char) is too small to hold all possible int values.

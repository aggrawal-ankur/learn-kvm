# Notes For The Reader

This code belongs to the Linux kernel. I have copied it locally to understand it.

I have annotated the code to understand it in depth.

The original LICENSE is available in the repository as it is.

---

The code was obtained with the following commands:
```bash
git clone --filter=blob:none --no-checkout --depth 1 --branch v7.2.6  \
  https://github.com/gregkh/linux.git linux-kvm-only

cd linux-kvm-only
git sparse-checkout init --no-cone

cat << 'EOF' > .git/info/sparse-checkout\
# Generic KVM Core\
/virt/kvm/\
\
# x86 KVM Core & Intel VT-x Driver\
/arch/x86/kvm/\
!/arch/x86/kvm/svm/\
\
# Platform x86 Virtualization\
/arch/x86/virt/\
!/arch/x86/virt/svm/\
\
# Crucial KVM Header Files (Contracts & Structs)\
/include/linux/kvm*\
/include/uapi/linux/kvm*\
/arch/x86/include/asm/kvm*\
/arch/x86/include/uapi/asm/kvm*\
EOF

git checkout
```

(obsessed with making compilers)

```asm
bits 32
global _start

_start:
  ; 14 - 8
  movq mm0, [a]
  paddb mm0, [b]
  movq [a], mm0

  ; = 6   - 4
  movq mm0, [a + 8]
  paddb mm0, [b + 8]
  movq [a + 8], mm0

  xor eax, eax
  mov al, 0x4
  xor ebx, ebx
  inc ebx
  mov ecx, a
  xor edx, edx
  mov dl, 14
  int 0x80

  xor eax, eax
  inc eax
  xor ebx, ebx
  int 0x80

section .data

a:
  db 36,55,22,16,30,10,59,16,10,50,50,60,10,5,0,0
b:
  db 36,50,22,16,43,29,50,16,87,58,51,60,23,5,0,0
```
(assembles with NASM and runs on Pentium MMX or better x86 machines with Linux)

Hey, I'm Alex and I like making programming languages.

```asm
bits 32
global _start

_start:
  ; 14 - 8
  movq mm0, [a]
  movq mm1, [b]
  paddb mm0, mm1
  movq [o], mm0

  ; = 6   - 4
  movd mm0, [a + 8]
  movd mm1, [b + 8]
  paddb mm0, mm1
  movd [o + 8], mm0

  ; = 2   - 2
  mov ax, [a + 12]
  mov bx, [b + 12]
  add ax, bx
  mov [o + 12], ax

  mov eax, 0x4
  mov ebx, 0x1
  mov ecx, o
  mov edx, 14
  int 0x80

  mov eax, 0x1
  xor ebx, ebx
  int 0x80

section .data

o:
  times 14 db 0
a:
  db 36,55,22,16,30,10,59,16,10,50,50,60,10,5
b:
  db 36,50,22,16,43,29,50,16,87,58,51,60,23,5
```
(assembles with NASM and runs on Pentium MMX or better x86 machines with Linux)

## Links:
- [Website](http://207.180.202.42/alex/)

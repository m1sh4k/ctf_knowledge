Для манипуляции отдельными битами числа ассемблер NASM предоставляет ряд логических операторов-инструкций:
```armasm
and source, dest
or source, dest
xor source, dest
neg dest
not dest
```

### and
Инструкция AND выполняет поразрядное логическое умножение.
```armasm
global _start
 
section .text
_start:
    mov rdi, 12       ; помещаем в регистр RDI число 12 - 1100
    and rdi, 6        ; rdi = rdi AND 6 = 1100 AND 0110 = 0100 = 4
    mov rax, 60
    syscall
```

### or
Инструкция OR выполняет поразрядное логическое сложение.
```armasm
global _start
 
section .text
_start:
    mov rdi, 12      ; помещаем в регистр rdi  число 12 - 1100
    or rdi, 6        ; rdi = rdi OR 6 = 1100 OR 0110 = 1110 = 14
    mov rax, 60
    syscall
```

### xor
Инструкция XOR выполняет поразрядную операцию исключающего ИЛИ.
```armasm
global _start
 
section .text
_start:
    mov rdi, 12      ; помещаем в регистр rdi  число 12 - 1100
    xor rdi, 6       ; rdi = rdi XOR 6 = 1100 XOR 0110 = 1010 = 10
    mov rax, 60
    syscall
```

### not
Инструкция NOT выполняет поразрядное отрицание и принимает один параметр:
```global _start
 
section .text
_start:
    mov rdi, 12     ; помещаем в регистр rdi число 12 - 00000000 00000000 00000000 00001100
    not rdi         ; rdi =NOT(rdi)=NOT(12)= 11111111 11111111 11111111 11110011
    mov rax, 60
    syscall
```

### neg
Кроме обычной инверсии в ассемблере есть арифметическое отрицацие, которое выполняет инструкция NEG. Она также принимает один операнд. фактически значение операнда будет умножаться на -1. Таким образом, мы сможем получить из положительного числа отрицательное, а из отрицательного - положительное.
```armasm
global _start
 
section .text
_start:
    mov rdi, -12
    neg rdi        ; rdi = -1 * rdi = -1 * -12 = 12
    mov rax, 60
    syscall
```
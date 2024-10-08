
## loop

Инструкция loop позволяют сократить определение цикла. Она уменьшает на 1 число в регистре RCX и переходит к определенной метке, если RCX не равен нулю.
```armasm
global _start
 
section .text
_start:
    mov rcx, 5      ; регистр-счетчик
    mov rdi, 0
mainloop:           ; цикл
    add rdi, 2      ; некоторые действия цикла
    loop mainloop   ; уменьшаем значение в rcx на 1, переходим к метке mainloop, если rcx не содержит 0
 
    mov rax, 60
    syscall
```

## jrczx

Выполнение цикла часто зависит от некоторого счетчика - если счетчик равен определенному значению (чаще 0), то выполнение цикла прекращается. Традиционно в качестве подобного регистра-счетчика используется регистр RCX. Так, инструкция `loop` из начала статьи проверяет данный регистр. И для упрощения проверки условия архитектура Intel x86-64 также предоставляет инструкцию jrcxz - она проверяет значение RCX, и если оно равно 0, то переходит к определенной метке.
```armasm
global _start
  
section .text
_start:
    mov rcx, 5      ; регистр-счетчик
    mov rdi, 1
mainloop:           ; цикл
    jrcxz exit      ; если rcx = 0, то переход к метке exit
    add rdi, 2      ; некоторые действия цикла
    loop mainloop  ; уменьшаем значение в rcx на 1, переходим к метке mainloop, если rcx не содержит 0
 
exit:
    mov rax, 60
    syscall
```
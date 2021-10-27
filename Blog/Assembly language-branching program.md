# Assembly language-branching program

## 题目

编写一个单字符加密程序，程序从键盘输入一个字符，经过加密后显示输出。加密 算法为：数字密文=原文循环加3，字母密文=原文循环加5。即0->31->4...7->08->19 既不是数字也不是学母的字符按原样输中。

## Tool:

> emu8086

## Structure:

![](https://cdn.jsdelivr.net/gh/Sophon3/Figure-bed/images2021/2021202110211343823.png)

## program:

```assembly
DATA SEGMENT ;SEGMENT是分段的逻辑标志
    str1 DB "PLEASE INPUT A NUMBER 0-9 OR A CHAR:$"
    str2 DB "OUTPUT:$"
    str3 DB "IF YOU WANT CONTINUE PLEASE ENTER THE #:$ "
    str4 DB "THIS PROGRAM IS OVER,THANKS:$"
    input DB '0'
    output DB '0'
    A DB '0'
DATA ENDS  ;SEGMENT以ENDS结束

CODE SEGMENT ;代码段
    ASSUME CS:CODE,DS:DATA ; 伪指令，告诉编译器段寄存器和段名之间的关系

START: 
        MOV AX,DATA
        MOV DS,AX
        
BEGIN:
        LEA DX,str1 ;输出字符串1
        MOV AH,9
        INT 21H
        
        MOV AH,1  ;从键盘输入一个字符
        INT 21H
        MOV BL,AL  ; 将接收到的字符转到BL寄存器中
        
        MOV DL,0DH  ;回车
        MOV AH,02H
        INT 21H
        MOV DL,0AH  ;换行
        MOV AH,02H
        INT 21H

        LEA DX,str2  ;输出字符串2
        MOV AH,9
        INT 21H
        
        MOV input,BL  ;赋值给input
        CMP input,'0' ;与0比较
        JL L
        CMP input,'9' ;与9比较
        JLE L1
        CMP input,40H
        JL L
        CMP input,'Z'
        JLE L2
        CMP input,60H
        JL L
        CMP input,'z'
        JLE L3

L:     ;L1标志，直接输出BL寄存器的值
        MOV output,BL
        MOV DL,output
        MOV AH,02H
        INT 21H     

L1:     ;L11标志,输出加密结果
        MOV BL,input
        ADD BL,03H
        MOV A,BL
        CMP A,'9' ;与9比较
        JG L11
        MOV output,BL
        MOV DL,output
        MOV AH,02H
        INT 21H
        JMP NEXT

L11: ;数字超出循环输出
        SUB BL,0AH
        MOV output,BL
        MOV DL,output
        MOV AH,02H
        INT 21H
        JMP NEXT

L2:     ;L2标志,输出加密结果
        MOV BL,input
        ADD BL,05H
        MOV A,BL
        CMP A,'Z' ;与Z比较
        JG CHARout
        MOV output,BL
        MOV DL,output
        MOV AH,02H
        INT 21H
        JMP NEXT


L3:     ;L2标志,输出加密结果
        MOV BL,input
        ADD BL,05H
        MOV A,BL
        CMP A,'z' ;与z比较
        JG CHARout
        MOV output,BL
        MOV DL,output
        MOV AH,02H
        INT 21H
        JMP NEXT

CHARout: ;字符超出循环输出
        SUB BL,1AH
        MOV output,BL
        MOV DL,output
        MOV AH,02H
        INT 21H
        JMP NEXT

NEXT: ;继续程序
        MOV DL,0DH  ;回车
        MOV AH,02H
        INT 21H
        MOV DL,0AH  ;换行
        MOV AH,02H
        INT 21H

        LEA DX,str3 ;输出提示字符串3
        MOV AH,09
        INT 21H
        
        MOV AH,1 ;接收一个字符
        INT 21H
        MOV BH,AL

        MOV DL,0DH  ;回车
        MOV AH,02H
        INT 21H
        MOV DL,0AH  ;换行
        MOV AH,02H
        INT 21H

        CMP BH,'#' ;判断用户输入的字符
        JE BEGIN
        JMP DOWN
    
DOWN:
    MOV DL,0DH  ;回车
    MOV AH,02H
    INT 21H
    MOV DL,0AH  ;换行
    MOV AH,02H
    INT 21H
    
    LEA DX,str4 ; 程序结束语
    mov ah,09
    INT 21h
    
    MOV AH,4CH ;结束
    INT 21H
CODE ENDS
    END START
```

## Computational results

![](https://cdn.jsdelivr.net/gh/Sophon3/Figure-bed/images2021/2021202110202149102.png)

## Konwledge point

>1. the string value need the $ in ending
>2. need to enter before you wrap,if you need "wrap"
>
>

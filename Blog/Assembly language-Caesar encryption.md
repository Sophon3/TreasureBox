# Assembly Language - Caesar encryption

题目

1、 编写循环结构程序

1. 单字符加密程序，该部分已在实验1实现。请将其编为一个子程序或一个宏指令。

2. 编制完整的汇编语言程序，实现从键盘输入一个原文字符串，将其加密后打印输出的功能。

3. 程序执行效果：

input: This is 7

output: Ymnx nx 0

4. 编程提示：

Input和output的消息提示用DOS系统功能09调用实现，输入字符串用0A调用实现，输出字符串用09调用实现。

在数据段中定义足够大小的数据输入和输出缓冲区。

主程序中的循环体实现：从输入缓冲区读一个字符->用子程序调用或宏指令调用对字符进行加密->加密字符存入输出缓冲区->修改字符指针。循环执行直至结束。

要利用和处理好字符串结束符’$’。输出格式调整时，要输出两个字符即回车符0DH，0AH。

```assembly
   DATAS SEGMENT
    STR1 DB "PLEASE INPUT A STRING:$"
    STR2 DB "               OUTPUT:$"
    STR3 DB "IF YOU WANT CONTINUE NETER THE /:$"
    BUF DB 20    ;预定义4字节
        DB '0'   ;输入完后自动获取输入的字符个数
        DB  20 DUP(0) ;初始化为0
    CODESTR DB 20 DUP('$')
    CRLF DB 0AH,0DH,"$"

DATAS ENDS

STACKS SEGMENT

STACKS ENDS

CODES SEGMENT
    ASSUME CS:CODES,DS:DATAS,SS:STACKS

START:
    MOV AX, DATAS  ;初始化数据
    MOV DS, AX
    CALL INPUTCODESTR
    CALL ENCODE 
    JMP EXIT

INPUTCODESTR PROC
    LEA DX, STR1
    MOV AH, 09H
    INT  21h
    LEA DX,BUF
    MOV AH, 0AH
    INT 21h
    MOV AL, BUF+1  ;给字符串末尾添加'$'结束符
    ADD AL, 2
    MOV AH, 0
    MOV SI, AX
    MOV BUF[SI],'$'  ;给字符串末尾添加'$'结束符

    LEA DX, CRLF
    MOV AH, 09H
    INT 21h
    RET
    
ENCODE PROC
    LEA SI,BUF+2
    LEA DI,CODESTR
    MOV CL,BUF+2
    MOV CH,0
    
ENCODE_AGAIN:
    MOV AL, [SI]
    CMP AL,'$'
    JE SHOWCODESTR

    CMP AL,'0'
    JL ENCODE_NEXT
    CMP AL,'9' ;与9比较
    JLE L1
    CMP AL,40H
    JL ENCODE_NEXT
    CMP AL,'Z'
    JLE L2
    CMP AL,60H
    JL ENCODE_NEXT
    CMP AL,'z'
    JLE L3
   

L1:
    ADD AL,03H
    CMP AL,'9'
    JG L11
    JMP ENCODE_NEXT
L11:
    SUB AL,0AH
    JMP ENCODE_NEXT
L2:
    ADD AL,05H
    CMP AL,'Z'
    JG CHAR
    JMP ENCODE_NEXT
L3:
    ADD AL,05H
    CMP AL,'z'
    JG CHAR
    JMP ENCODE_NEXT

CHAR:
    SUB AL,1AH
    JMP ENCODE_NEXT

ENCODE_NEXT:
    MOV [DI],AL
    INC SI
    INC DI
    LOOP ENCODE_AGAIN


SHOWCODESTR:
    LEA DX,STR2
    MOV AH,09H
    INT 21h
    LEA DX,CODESTR
    MOV AH,09H
    INT 21h
    RET
   
EXIT:
    MOV AH, 4CH
    INT 21h
CODES ENDS
    END START
```


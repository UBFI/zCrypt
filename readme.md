# What is zCrypt?
zCrypt is a C array obfuscation technique using randomized bitwise operations of C arrays at runtime.
It's main purpose is to hide strings and shellcode arrays from automated analysis. A hosted version can be accessed [here](https://ubfi.github.io/zCrypt/index.html).
# What are rounds?
Each round is a bit shift which adds an extra instruction to the 'de-obfuscation' process. This can make reverse engineering or automated detection more difficult!
# How do I use it?
A good example it to use msfvenom to generate an array and converting is using the C format when generating.

## Disable Stack Protection using mingw-w64 for Windows PEs
>x86_64-w64-mingw32-gcc main.c -o main.exe -fno-stack-protector -z execstack

## Disable Stack Protection using GCC for Linux ELFs
>gcc main.c -o main -fno-stack-protector -z execstack -no-pie

## Disable Stack Protection in Visual Studio for Windows PEs
Open your project in Visual Studio.
Right-click on your project in the Solution Explorer and select "Properties." ->
In the project properties window, navigate to the "Configuration Properties" section. ->
Open the "C/C++" category and select "Code Generation." ->
In the right-hand pane, locate the "Buffer Security Check" option. ->
Change the value of "Buffer Security Check" to "No (/GS-)" to disable stack protection. ->
Click "Apply" and then "OK" to save the changes. Profit!

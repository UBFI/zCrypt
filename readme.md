# What is zCrypt?
zCrypt is a C array obfuscation technique using randomized bitwise operations of C arrays at runtime. 
Every generation will be unique and have a completely random sequence. zCrypt also uses very little static code so it is very difficult to detect its usage.<br>
"zcrypt.html" is a javascript based client-side application to create obfuscated arrays.<br>
It's main purpose is to hide strings and shellcode arrays from automated analysis.<br>
A hosted version can be accessed [here](https://ubfi.github.io/zCrypt/index.html).
# What are rounds?
Each round is a randomly bit-wise operation added to the final 'de-obfuscation' process when the binary is executed.<br>
This can make reverse engineering or automated detection more difficult as scantime will not contain the final array or strings.
# How do I use it?
A good example it to use msfvenom to generate an array and converting is using the C format when generating.<br>
You can also use the strings function with something like 'start calc.exe' then checking the binary for the string.

## Disable Stack Protection using mingw-w64 for Windows PEs
>x86_64-w64-mingw32-gcc main.c -o main.exe -fno-stack-protector -z execstack

## Disable Stack Protection using GCC for Linux ELFs
>gcc main.c -o main -fno-stack-protector -z execstack -no-pie

## Disable Stack Protection in Visual Studio for Windows PEs
- Open your project in Visual Studio.
- Right-click on your project in the Solution Explorer and select "Properties." ->
- In the project properties window, navigate to the "Configuration Properties" section. ->
- Open the "C/C++" category and select "Code Generation." ->
- In the right-hand pane, locate the "Buffer Security Check" option. ->
- Change the value of "Buffer Security Check" to "No (/GS-)" to disable stack protection. ->
- Click "Apply" and then "OK" to save the changes. Profit!

# Gdb baby step 1

*Flag:* picoCTF{549698}

How you approached the challenge:

- step 1: I personally dont have much experience in reverse engineering and so after the question when i tried to read contents it was not readable so i even checked the file type by writing file debugger0_a but didnt give me much idea so  i opened first hint and there they told to use gdb compiler so i did gdb debugger0_a and then i checked the second hint it said to use commands to get main or something so i went to chatgpt and searched up commands in gdb to get main one particular command said (gdb) dissassemble main this caught my eye since in the question they told to diassemble it. On writing that i got many values and there was only one value written like this $0x86342,%eax and so i was sure this value was it i took this value and went to hex to decimal converter because they wanted answer in decimal and ye got it!!
![image](https://github.com/user-attachments/assets/242450e8-a3dd-428b-9e94-c86c501c1e67)


- step 2:
```
root@Krish:~# wget https://artifacts.picoctf.net/c/512/debugger0_a
--2024-11-06 00:04:42--  https://artifacts.picoctf.net/c/512/debugger0_a
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 18.67.161.101, 18.67.161.51, 18.67.161.65, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|18.67.161.101|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16472 (16K) [application/octet-stream]
Saving to: ‘debugger0_a’

debugger0_a                   100%[=================================================>]  16.09K  --.-KB/s    in 0s

2024-11-06 00:04:43 (367 MB/s) - ‘debugger0_a’ saved [16472/16472]

root@Krish:~# cat debugger0_a
@@@@�����   00�-�=�= (.>>�888 XXXDDS�td888 P�td   <<Q�tdR�td�-�=�=/lib64/ld-linux-x86-64.so.2GNU�GNU���,��
                                                                                                          <�
                                                                                                            ��}\��GNU��e�m8 ␦T c
         "libc.so.6__cxa_finalize__libc_start_mainGLIBC_2.2.5_ITM_deregisterTMCloneTable__gmon_start___ITM_registerTMClo�H�=��r/�H�=�/H��/H9�tH�N/H��t�������H�=i/H�5b/H)�H��H��?H��H�H��tH�%/H����fD�����=%/u+UH�=/H��t
                                                                                                H�=/�)����d�����.]������w�����UH��}�H�u�B]Ð��AWL�=�,AVI��AUI��ATA��UH�-�,SL)�H�����H��t1��L��L��D��A��H��H9�u�H�[]A\A]A^A_�ff.������H�H��8���l,����<���T%����<��������zRx


                        ����/D$4����FJ
M                                     �?␦:*3$"\����tq���E�C
D�h���eF�I�E �E(�D0�H8�G@n8A0A(B BB����� �
��␦����o�X�
}
 �?    ������o����o���o����o@GCC: (Ubuntu 9.4.0-1ubuntu1~20.04.1) 9.4.08X|���   �


0@�  @ �=�=>�?@@��
                  p�!�7@F�=m y�=������,!����=�>��=� ��?�

�␦ ^ @6@�=\@i @� �@e�@b@/�@�)�@� �"crtstuff.cderegister_tm_clones__do_global_dtors_auxcompleted.8061__do_global_dtors_aux_fini_array_entryframe_dummy__frame_dummy_init_array_entrydebugger0_a.c__FRAME_END____init_array_end_DYNAMIC__init_array_start__GNU_EH_FRAME_HDR_GLOBAL_OFFSET_TABLE___libc_csu_fini_ITM_deregisterTMCloneTable_edata__libc_start_main@@GLIBC_2.2.5__data_start__gmon_start____dso_handle_IO_stdin_used__libc_csu_init__bss_startmain__TMC_END___ITM_registerTMCloneTable__cxa_finalize@@GLIBC_2.2.5.symtab.strtab.shstrtab.interp.note.gnu.property.note.gnu.build-id.note.ABI-tag.gnu.hash.dynsym.dynstr.gnu.version.gnu.version_r.rela.dyn.init.plt.plt.got.text.fini.rodata.eh_frame_hdr.eh_frame.init_array.fini_array.dynamic.data.bss.comment#886XX$I|| W���o��a
                                                ��iXX}q���o��
�  �  <�@ @ �����>.��?��@@00+@0�6�8                          ~���o��  �00�@@u���
```
```
root@Krish:~# file debugger0_a
debugger0_a: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=15a10290db2cd2ec0c123cf80b88ed7d7f5cf9ff, for GNU/Linux 3.2.0, not stripped
```                                
```
root@Krish:~# gdb debugger0_a
GNU gdb (Ubuntu 12.1-0ubuntu1~22.04.2) 12.1
Copyright (C) 2022 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Type "show copying" and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<https://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
    <http://www.gnu.org/software/gdb/documentation/>.

For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from debugger0_a...
(No debugging symbols found in debugger0_a)
(gdb) disassemble main
Dump of assembler code for function main:
   0x0000000000001129 <+0>:     endbr64
   0x000000000000112d <+4>:     push   %rbp
   0x000000000000112e <+5>:     mov    %rsp,%rbp
   0x0000000000001131 <+8>:     mov    %edi,-0x4(%rbp)
   0x0000000000001134 <+11>:    mov    %rsi,-0x10(%rbp)
   0x0000000000001138 <+15>:    mov    $0x86342,%eax
   0x000000000000113d <+20>:    pop    %rbp
   0x000000000000113e <+21>:    ret
End of assembler dump.
```
What you learned through solving this challenge:

1. Got an idea about gdb compiler or GNU debugger

Other incorrect methods you tried:

- I tried reading contents of file without checking the type of file

References

- https://www.rapidtables.com/convert/number/hex-to-decimal.html?x=86342

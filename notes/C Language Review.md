I already have a good amount of experience coding in C, but good to have a review and learn how to use it with embedded systems.

# C Language: General Terms and Concepts
* **Compiler** converts high-language language to assembly
	* translate one **translation  unit** (e.g., a c file) to assembly
* **Assembler** converts assembly to machine code (binary)
	* Assemble the compilers output into a **object file** which organizes data and machine code into a well known format to be manageable and understandable by the different tools and developer
* Program moves through **linking** (object file --> executable) and **loading** (disk --> RAM) before CPU executes it
	* **Linker:** takes multiple object files and merges them into a single executable file like a .exe file on Windows or an ELF file on Linux.
	* **Loading:** OS reads the executable file header and sets up virtual address space for the process, allocates space in RAM for the text (code), data, and stack segments, and copies the machine bytes from storage into memory.

**ELF:** An object file format used for executables, object code, shared libraires, device drivers, and core dumps on Linux or Unix-like OSs


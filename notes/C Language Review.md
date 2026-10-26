I already have a good amount of experience and knowledge with the language C/C++, but good to have a review and learn how to use it with embedded systems.

# Compile, Assemble, and Link
Build Process (compile, assemble, and link):
* **Compiler** converts high-language language (.c files) to assembly
	* translate one **translation unit** (e.g., a c file) to assembly
* **Assembler** converts assembly (.s files) to machine code (binary)
	* Assemble the compilers output into a **object file** which organizes data and machine code into a well known format to be manageable and understandable by the different tools and developer
* Program moves through **linking** (object file --> executable) and **loading** (disk --> RAM) before CPU executes it
	* **Linker:** takes multiple object files and merges them into a single executable file like a .exe file on Windows or an ELF file on Linux.
		* The .o object files are **relocatable object files** --> once they are all linked into one, the file is called the **executable object file** 
			* This process is specified in a **linker script**
	* **Loading:** OS reads the executable file header and sets up virtual address space for the process, allocates space in RAM for the text (code), data, and stack segments, and copies the machine bytes from storage into memory.

**ELF:** An object file format used for executables, object code, shared libraires, device drivers, and core dumps on Linux or Unix-like OSs. The format of the executable object file is also ELF.
* To execute, Linux Kernel uses a **ELF loader** that reads and loads the ELF you want to execute into memory.

# Objects and Identifiers 
**Object:** Region of data storage
* Have different properties that 
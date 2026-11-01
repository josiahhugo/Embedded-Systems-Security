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
**Object:** Region of data storage -- piece of memory that holds a value(s)
* Have different properties that influence how they are handled during the build process.
* Ex: `int count = 10;` --> memory is allocated to store the integer 10 is an object

**Identifier:** Name assigned by a programmer to program an element such as a variable, function, array, structure, or label
* Ex: `int total_score = 95;` where `total_score` is the identifier
* Can only be used in the scope it is visible and often it is even destroyed when its scope ends

**Scope:** Region or portion of the source code where a declared identifier is valid and can be accessed to refer to its entity
* Is an implicit property of an identifier

Objects as functions, enums, structs, etc. are denoted by a **identifier** --> has a **scope** which is the portion of source it is **visible**
Typs of scopes:
* **Block scope**: Identifier is declared inside a compound statement like a function body, `if` statement or `loop` and is only accessible from its point of declaration
* **File scope**: Identifier is declared outside of any functions or block and is visible from its point of declaration to the end of the translation unit (source file)
* **Function scope**: Applies strictly to labels which are visible anywhere inside the function they are declared in, regardless of block nesting 


**Storage Class:** can be changed to influence the visibility and lifetime of an object. There are 2 specifiers that influence 2 properties (linkage and storage duration):
* **Extern**: external linkage, static duration
	* **external linkage**: variable can be used from scopes in other translation units
* **Static**: internal linkage, static duration
	* variable lives through the whole program lifetime, not only in a block scope or function
	* **internal linkage**: object can be used in all scopes of the current translation unit

**Static Duration:** object or variable is allocated in memory when the program starts running and is freed only when program terminates --> variable that lives through the whole program 

**Linkage:** variable can be used in other scopes

Identifiers can be in 3 states:
* **Declared**: Introduces name and type of an identifier to the compiler without necessarily allocating memory or reserving storage for it
	* ex: `int a;`  
	    `struct myStruct;` 
* **Defined**: allocates actual storage or memory in the computer for the identifier based on its data type
	* ex: `int a;` 
		`struct myStruct {...};`
* **Initialized**: it is a definition combined with the assignment of a starting (initial) value at the moment it is created
	* ex: `a = 1;` 
		`myStruct = {...};`

# Compiler, Assembler and Linker
**Section:** range of addresses in a memory region
* Used on both relocatable object file and executable object file level
* all machine code and data from one translation unit ends in sections of the relocatable object file

**Link Step:** When executable object file is linked
* **Input sections**: Input from relocatable object files are joined into...
* **Output sections**: output to executable object file

**Linker Script:** when sections from the object file are joined into which sections of the executable 

**Symbols:** Used as an umbrella term for different kind of symbols:
* **Directive**: (Pseudo-Instruction) Commands written in assembly code that give instructions directly to the assembler rather than the CPU.
	* determined by "." in front of a symbol
	* ex: `.word variable 1`
* **Assembly Instructions**: (Machine Instructions) Low-level commands that correspond directly to native machine code executed by the processor (CPU)
	* ex: `R1, #1`
* **Labels**: User-defined text identifiers placed at specific lines or memory addresses in the code
	* determined by ":" following a symbol
	* ex: `label1: `

**Statements:** Consist of an optional label and a directive or an assembler instruction
* ex: `myLabel:
	    `ADD X1, X2`
	or
	`myLabel:
		`.text` 

# ELF
Life of an ELF file consists of 2 important tasks:
* Structure data and machine code during the build process --> important in the linking step of the building process
* Structure data and machine code for execution
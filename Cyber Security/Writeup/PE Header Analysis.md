
> All header is a Struct data type.

# IMAGE_DOS_HEADER

> The IMAGE_DOS_HEADER consists of the first 64 bytes of the PE file.


### Values

__e_magic__ : Common have a `MZ` refer to [Mark Zbikowski](https://en.wikipedia.org/wiki/Mark_Zbikowski),
__e_lfanew__ : Contain the address of `IMAGE_NT_HEADERS` start.

# DOS_STUB

> it just contain a message run of PE don't compatible with the machine you try to run PE on it.

# IMAGE_NT_HEADERS

## NT_HEADERS

- __Signature__: The first 4 bytes of the `NT_HEADERS`, The Signature denotes the start of the `NT_HEADER`
- FILE_HEADER
	- _Machine:_ This field mentions the type of architecture for which the PE file is written.
	- _NumberOfSections:_ A PE file contains different sections where code, variables, and other resources are stored.
	- _TimeDateStamp:_ This field contains the time and date of the binary compilation.
	- _PointerToSymbolTable and NumberOfSymbols:_ These fields are not generally related to PE files.
	- _SizeOfOptionalHeader:_ This field contains the size of the optional header
- OPTIONAL_HEADER
	- _Magic:_ The Magic number tells whether the PE file is a 32-bit or 64-bit application.
		- 0x010B: 32-bit
		- 0x020B: 64-bit
	- _AddressOfEntryPoint_:  This is the address from where Windows will begin execution.
	- BaseOfCode and BaseOfData: These are the addresses of the code and data sections, respectively, relative to Image Base.
	- _Image Base:_ The Image Base is the preferred loading address of the PE file in memory.
	- _Subsystem:_ This represents the Subsystem required to run the image.


## IMAGE_SECTION_HEADER

- _.text:_ The .text section is generally the section that contains executable code for the application.
- _.data:_ This section contains initialized data of the application.
- ._rdata/.idata:_ These sections often contain the import information of the PE file.
-  .ndata: The .ndata section contains uninitialized data.
- _.rsrc:_ The resource section contains icons, images, or other resources required for the application UI.



## Tools

1. WXhexeditor
2. pe-tree
3. peckeck
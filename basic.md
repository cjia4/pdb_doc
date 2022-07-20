## PDB's 'stream' concept. 

| Stream No.			| Contents																								|Short Description
|--------------|---------------------------------|-------------------
| 1            | Pdb (header)	                   | Version information, and information to connect this PDB to the EXE
| 2	           | Tpi (Type manager)	             | All the types used in the executable.
| 3	           | Dbi (Debug information)	        | Holds section contributions, and list of ‘Mods’
| 4	           | NameMap	                        | Holds a hashed string table
| 4-(n+4)	     | n Mod’s (Module information)	   | Each Mod stream holds symbols and line numbers for one compiland
| n+4	         | Global symbol hash	             | An index that allows searching in global symbols by name
| n+5	         | Public symbol hash	             | An index that allows searching in public symbols by addresses
| n+6	         | Symbol records	                 | Actual symbol records of global and public symbols
| n+7	         | Type hash	                      | Hash used by the TPI stream.

| Name	| Stream Index	| Contents|
|--|--|--|
|Old Directory	| Fixed Stream Index 0 | Previous MSF Stream Directory
|PDB Stream	| Fixed Stream Index 1 |  Basic File Information
|           |                      | Fields to match EXE to this PDB
|           |                      | Map of named streams to stream indices 
|TPI Stream	| Fixed Stream Index 2 | CodeView Type Records
|           |                      | Index of TPI Hash Stream
|DBI Stream	| Fixed Stream Index 3 | Module/Compiland Information
|           |                      | Indices of individual module streams
|           |                      | Indices of public / global streams
|           |                      | Section Contribution Information
|           |                      | Source File Information
|           |                      | References to streams containing FPO / PGO Data
|IPI Stream	| Fixed Stream Index 4 | CodeView Type Records
|           |                      | Index of IPI Hash Stream
| /LinkInfo	| Contained in PDB Stream Named Stream map | Unknown
| /src/headerblock	| Contained in PDB Stream Named Stream map | Summary of embedded source file content (e.g. natvis files)
| /names| Contained in PDB Stream Named Stream map | PDB-wide global string table used for string de-duplication
| Module Info Stream | Contained in DBI Stream | CodeView Symbol Records for this module
|  | One for each compiland | Line Number Information
| Public Stream	| Contained in DBI Stream | Public (Exported) Symbol Records
| | | Index of Public Hash Stream
| Global Stream	| Contained in DBI Stream | Single combined symbol-table
| | |Index of Global Hash Stream
|TPI Hash Stream | Contained in TPI Stream | Hash table for looking up TPI records by name
| IPI Hash Strea| Contained in IPI Stream | Hash table for looking up IPI records by name

## obj 
| section | comment |  description |
|------|---------------------|---
| .debug\$T | "types" section |  contains CodeView records that describe all of the data types referenced by symbols in that .obj |
| .debug\$S | "symbols" section | contains CodeView records that describe all of the symbols defined within the .obj, including functions, global and static data, and local variables |


## version 7.0
signature is GUID-like
    
[PDB format has several versions](https://github.com/microsoft/microsoft-pdb/blob/082c5290e5aff028ae84e43affa8be717aa7af73/langapi/include/pdb.h#L104)

| Term  |  interpretation |
|-------|-----------------|
| TI    | type index       |
| MSF   | Multiple Stream File |
GSI
TPI Type info
NB10 

PDBOpen2W

# Reference:
1. https://github.com/Microsoft/microsoft-pdb
2. https://lists.llvm.org/pipermail/cfe-dev/2015-October/045780.html
3. https://llvm.org/docs/PDB/CodeViewTypes.html
4. https://llvm.org/doxygen/namespacellvm_1_1codeview.html
5. https://github.com/luser/dump_syms/blob/master/PDBParser.cpp
6. https://docs.rs/pdb/latest/pdb/
7. https://reviews.llvm.org/rG89ba802b92883c2237130ca6f3dfe19499efd1f4
8. https://llvm.org/docs/PDB/TpiStream.html#type-indices
9. https://llvm.org/docs/PDB/PdbStream.html
10. [stream description](https://llvm.org/docs/PDB/index.html)


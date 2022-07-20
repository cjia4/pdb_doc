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

## version 7.0
signature is GUID-like
    
[PDB format has several versions](https://github.com/microsoft/microsoft-pdb/blob/082c5290e5aff028ae84e43affa8be717aa7af73/langapi/include/pdb.h#L104)



# Reference:
1. https://github.com/Microsoft/microsoft-pdb

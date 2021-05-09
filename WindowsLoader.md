# How how PE  loader finds out the address of functions exported by DLL

- Loader takes the PE header of DLL and parse it to get to the Export Directory. Export Directorry 
have a structure. Name of the structure is *_IMAGE_EXPORT_DIRECTORY*. This structure contains information about the export directory. Some of main
info are: a) Name-->Name of DLL b) Base-->First ordinal number c)AddressOfFunctions-->export address table
d) AddressofNames-->pointer to names e) AddressOfNameOrdinals-->gives the ordinal number of function
which means serial number of function in AddressOfFunctions. same can be crosss confirmed any PE file reader or in the header files
- A DLL can export functions by 2 ways
 a) By name
 b) By ordinal number--> "Base", member of export table structure holds the  first ordinal which is exported from the DLL.
 
 - How loader is going to get address of a particular function that is exported by name: First, Loader is going to check the "AddressOfName" array for the function name.
 If it finds the function name then it saves the index number at which the function name was. Each entry in "AddressOfNames" array is of 4 bytes. Now the loader will move 
  to "AddressOfNameOrdinals" array. There the loader will move to the index saved from traversal of "AddressOfNames" array. At that particular index loader will find a ordinal number.
 At last loader will traverse "AddressOfFunction" array. Loader will move to the will tke the save ordinal number as index and will mmove that particular index in "AddressOfFunction" array.
 There loader will find the address of function.
 

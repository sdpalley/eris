# How to create spider webs

The API for the Structural contracts are as follows:

*Note* this is NOT the API of the final c3D contract system. In the final product, these commands will be filtered through the Bylaws and the Bylaws will call these commands -- not the caller. This set of API commands are only for testing c3D in isolation (without a DOUG attached). To use this API structure, create a c3D web by hand and then test your spiders on it.

To deploy these contracts you will use the non-factory contracts from the contracts directory.

### Initialize

"init" (datamodel.JSON) (UI Structure) 0xOwnerAddress

When testing in isolation, don't worry about the `OwnerAddress` because the only place used in the testing contracts are commented out -- you can stick something in there if you want, or just leave blank.

### Set a Parent

"bind" 0xParentAddress

### Add Link

"addlink" (linkID) (main) (type) (content) (datamodel.JSON) (UIstructural)

These fields correspond to the fields listed in the `Compatibility Docs.md` file

*Note* `linkID` is determined in the c3D layer, not in the ethereum layer. It is the responsibility of the c3D client to avoid collisions. If a duplicate `linkID` is sent to the contract, the contract will simply not accept it. A handy trick is add 0 to the end of the `linkID` just to ensure there are at least 16 slots separating linked list entries which is more then sufficient.

### Remove Link

"rmlink" (linkID)

Does what it says.
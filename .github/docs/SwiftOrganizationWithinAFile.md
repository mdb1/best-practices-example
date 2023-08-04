# Swift's Organization Within a File

## How do we organize files?
A file should only contain one major type declaration. Other types are allowed in support of the main type that is represented by the file, which typically shares the name of the file, e.g. `LoginViewController.swift` would have a major type of `LoginViewController`.

### Key Considerations
* Files are organized in the following order:
	* Default header created by Xcode
	* Import statements
	* Protocols that are associated primarily with the major type declaration of the file.
	* The major type declaration of the file
	* Nested type declarations
	* Properties
        * Public propertyWrappers
	    * Public properties
	    * Internal propertyWrappers
        * Internal properties
	    * Private properties
    * Initializer
    * Public Extensions
    * Extension protocol conformances
    * Internal Extensions
    * Private Extensions
	
* Initializers, when implemented, should be the first declaration(s) in each group (inherited, protocol, open, etc.) of functions.
* For `Codable` conformance, [it may be necessary to implement the special nested type `CodingKeys`, which conforms to `CodingKey`](https://developer.apple.com/documentation/foundation/archives_and_serialization/encoding_and_decoding_custom_types). When present, this nested type should be declared after all other nested types.
* Default protocol implementation extensions should never include additional methods or properties unless they are `private` to the extension and only used in the default implementation(s).
* Inside the extensions:
  * First the computed properties
  * Then the methods

### How do we use MARK?
We don't use MARK comments.
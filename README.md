## Introduction
GIDL **translates between the Interface Definition Languages (IDLs)** of the following messaging frameworks:
- Simple Binary Encoding (SBE)
- Apache Thrift
- Google FlatBuffers
- Google Protocol Buffers (ProtoBuf)
- Cap'n Proto (capnp)

GIDL uses XML because:
- XML is easy to extend, unknown elements are ignored.
- XML is widely understood.
- XML is supported in most programming languages, so translators can be written in different languages.
- XML eases modeling tool integration.
- For the purpose of translating between IDLs, the weak performance of XML is a non-issue.

GIDL serves several purposes:
- simplifies migration between the four messaging frameworks
- enables modeling tool integration
- allows easy performance comparisons between the messaging frameworks

## Translating messaging concepts

### Basic types
GIDL translates basic types as follows:

GIDL    |SBE     |Thrift |ProtoBuf                |FlatBuffers |Capnp   |Comment
--------|--------|-------|------------------------|------------|--------|----
bool    |(bit)set|bool   |bool                    |bool        |Bool    |like Java boolean
char8   |char    |-      |-                       |-           |-       |Signed 8-bit char
sint8   |int8    |byte   |-                       |byte        |Int8    |Signed
sint16  |int16   |i16    |-                       |short       |Int16   |Signed
sint32  |int32   |i32    |sint32, sfixed32, int32 |int         |Int32   |Signed
sint64  |int64   |i64    |sint64, sfixed64, int64 |long        |Int64   |Signed
uint8   |uint8   |-      |-                       |ubyte       |UInt8   |Unsigned
uint16  |uint16  |-      |-                       |ushort      |UInt16  |Unsigned
uint32  |uint32  |-      |uint32, fixed32         |uint        |UInt32  |Unsigned
uint64  |uint64  |-      |uint64, fixed64         |ulong       |UInt64  |Unsigned
float32 |float   |-      |float                   |float       |Float32 |like Java float
float64 |double  |double |double                  |double      |Float64 |like Java double


### String/blob types
GIDL translates string/blob types as follows:

GIDL    |SBE     |Thrift |ProtoBuf |FlatBuffers |Capnp   |Comment
--------|--------|-------|---------|------------|--------|----
data    |data    |binary |bytes    |-           |Data    |Binary blob, sequence of bytes
string  |-       |string |string   |string      |Text    |Blob with character encoding (e.g. UTF-8)


### Complex types
GIDL translates the complex type concepts as follows:

GIDL   |SBE       |Thrift    |ProtoBuf |FlatBuffers |Capnp   |Comment
-------|----------|----------|---------|------------|--------|------------------------
struct |composite |-         |-        |struct      |group   |set of fields that are encapsulated
enum   |enum      |enum      |enum     |enum        |enum    |wow, the only concept present in all IDLs
map    |-         |map       |map      |-           |-       |like Java Map
list   |group     |list      |repeated |vector      |List(T) |like Java List
union  |-         |union     |oneof    |union       |union   |like C union (alternative space)
typedef|type      |typedef   |-        |-           |using   |Renaming primitive types
void   |-         |void      |void     |-           |Void    |like Java void, only needed for services/interfaces
const  |-         |const     |-        |-           |const   |constant value

The following type concepts were introduced with programming language support or tool support in mind, not focusing on the messaging aspect.
Therefore, they are simplified using the messaging focus only:
- Apache Thrift: "set" is simplified using "list".
- Apache Thrift: "exception" is simplified using "struct" combined with "string".
- Google FlatBuffers: "root_type" is ignored.
- SBE: "field" serves to identify fixed size fields of a message, this is done with a "length" attribute in GIDL.

### Messages
GIDL translates the message concepts as follows:

GIDL      |SBE               |Thrift    |ProtoBuf    |FlatBuffers     |Capnp         |Comment
----------|------------------|----------|------------|----------------|--------------|-----------------
message   |message           |struct    |message     |table           |struct        |encapsulates one transmitted message
reference |-                 |reference |reference   |reference       |reference     |references to another message/struct/table


## Translating remote service concepts
Messages are the basic building blocks of remote services. However, looking at the detail: building remote services needs more than just messages only. 
We need to be able to construct three main types of remote services:
1. unidirectional services
2. bidirectional asynchronous services
3. bidirectional synchronous services

There are two different approaches how to construct remote services:
1. unique file IDs, in combination with struct/message/table names
2. service definitions,  

Both approaches can be applied - but building bidirectional remote services is more difficult without service definitions:
* Bidirectional service methods consist of both request messages and response messages. To clarify which two messages form the service together, one might add the suffixes "Request" and/or "Response" to both messages forming one service.
* Services with many different methods (e.g. an API) are difficult to define, especially when the request message type is the same for some methods.
* One way to fix this is to split these service methods into different files. Thus, the unique file IDs are used to show which service method is meant. This way, the request message names can be the same, but their definitions are in effect the same. this leads to code redundancy and violates the DRY principle.
* Another way to fix this is to duplicate the request messages in the same file, giving them different message names. This again leads to code redundancy and violates the DRY principle.r
GIDL translates the different service concepts as follows
GIDL      |SBE               |Thrift    |ProtoBuf    |FlatBuffers     |Capnp         |Comment
----------|------------------|----------|------------|----------------|--------------|-----------------
service   |-                 |service   |service     |-               |interface     |collection of service methods
schema    |message schema    |-         |-           |-               |-             |Root XML element
fileId    |message schema id |-         |-           |file_identifier |@ (unique id) |unique file IDDeThe missing "service" concept in  SBE and FlatBuffers is inconvenient currently, but it is always possible to add a "service" concept later on.
This will improve readability, maintainability, clarity and usability. It is clear that this is not a performance argument, but a software engineering argument solely..

## Please help and contribute
GIDL is an exciting work in progress..
Please feel welcome to contribute to GIDL!!
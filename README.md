# Migrate to low-latency messaging conveniently

## What is GIDL?
GIDL **translates between the Interface Definition Languages (IDLs)** of these messaging frameworks:
- Apache Thrift - **medium latency**
- Google Protocol Buffers (ProtoBuf) - **medium latency**
- Simple Binary Encoding (SBE) - **low latency**
- Google FlatBuffers - **low latency**
- Cap'n Proto (capnp) - **low latency**

## Why GIDL?
Reasons to use GIDL:
- Simplify migration between messaging frameworks
- Speed up modeling tool integration
- Ease performance comparisons between the messaging frameworks

## Documentation
[Design principles](Design principles)

[Translating message definitions](Translating message definitions)

[Translating service definitions](Translating service definitions) *in combination with* [Service workarounds for SBE and FlatBuffers](Service workarounds for SBE and FlatBuffers)

[Suggesting improvements for generated Java clients](Suggesting improvements for generated Java clients)

[GIDL roadmap](GIDL roadmap)

## Please help and contribute
GIDL is an exciting work in progress.

Please feel very welcome to contribute to GIDL, just write an e-mail to Andreas at gidl-community@gmx.de 
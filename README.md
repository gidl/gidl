# Migrate to low-latency messaging conveniently

## What is GIDL?
GIDL **translates between the Interface Definition Languages (IDLs)** of these messaging frameworks:
- Simple Binary Encoding (SBE) - **low latency (LOLA)**
- Google FlatBuffers - **low latency (LOLA)**
- Cap'n Proto (capnp) - **low latency (LOLA)**
- Apache Thrift - **medium latency**
- Google Protocol Buffers (ProtoBuf) - **medium latency**

## Why GIDL?
Some reasons to use GIDL:
- Migrate to low-latency (LOLA) messaging frameworks conveniently
- Allow performance comparisons between different messaging frameworks

## Documentation
[Design principles](https://github.com/gidl/gidl/wiki/Design-principles)

[Translating type definitions](https://github.com/gidl/gidl/wiki/Translating-type-definitions)

[Translating message and service definitions](https://github.com/gidl/gidl/wiki/Translating-message-and-service-definitions) *in combination with* [Service workarounds for SBE and FlatBuffers](https://github.com/gidl/gidl/wiki/Service-workarounds-for-SBE-and-FlatBuffers)

[GIDL roadmap](https://github.com/gidl/gidl/wiki/GIDL-roadmap)

# Project dependencies
**Simple binary encoding** (by Real Logic):
- Project page: https://real-logic.github.io/simple-binary-encoding/
- Project repository on GitHub: https://github.com/real-logic/simple-binary-encoding
- Apache 2.0 license: https://github.com/real-logic/simple-binary-encoding/blob/master/LICENSE

**Google FlatBuffers** (by Google):
- Project page: https://google.github.io/flatbuffers/
- Project repository on GitHub: https://github.com/google/flatbuffers
- Apache 2.0 license: https://github.com/google/flatbuffers/blob/master/LICENSE.txt

**Cap'n Proto** (by Sandstorm.io):
- Project page: https://capnproto.org/
- Project repository on GitHub: https://github.com/sandstorm-io/capnproto
- MIT license: https://github.com/sandstorm-io/capnproto/blob/master/LICENSE

**Apache Thrift** (by Apache Foundation):
- Project page: https://thrift.apache.org/
- Project repository: https://git-wip-us.apache.org/repos/asf?p=thrift.git;a=summary
- Apache 2.0 license: http://www.apache.org/licenses/

**Google Protocol Buffers** (by Google):
- Project page: https://developers.google.com/protocol-buffers/
- Project repository on GitHub: https://github.com/google/protobuf
- Apache 2.0 license: https://github.com/google/flatbuffers/blob/master/LICENSE.txt

## Please help and contribute
GIDL is an exciting work in progress, but I can't spend much time on it.

Please feel very welcome to contribute to GIDL! Consult the [GIDL roadmap](https://github.com/gidl/gidl/wiki/GIDL-roadmap) on how to help - and just write a quick e-mail to Andreas Schmid at gidl-community@gmx.de 
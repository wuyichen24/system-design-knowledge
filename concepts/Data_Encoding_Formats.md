# Data Encoding Formats

| Name | Base | Concept | Schema | Pros | Cons | Use cases |
|----|----|----|-----|----|----|----|
| XML | Text | Extensible Markup Language | Optional | <li>Good support for Unicode character strings | <li>Verbose and complicated<li>Cannot distinguish between a number and a string<li>Cannot support binary strings | | 
| JSON | Text | JavaScript Object Notation | Optional | <li>Lightweight<li>Human-readable<li>Can distinguish between a number and a string<li>Good support for Unicode character strings<li>Built-in support in web browsers | <li>Cannot support binary strings | |
| CSV | Text | Comma-Separated Values | Optional |
| TSV | Text | Tab-Separated Values | Optional |
| Protocol Buffers | Binary | | Required |
| Thrift | Binary | | Required |
| Avro | Binary | | Required |
| BSON | Binary | | |
| CBOR | Binary | | |

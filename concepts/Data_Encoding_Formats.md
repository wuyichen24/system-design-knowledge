# Data Encoding Formats

| Name | Base | Concept | Schema | Pros | Cons | Use cases |
|----|----|----|-----|----|----|----|
| XML | Text | Extensible Markup Language | Optional | <li>Good support for Unicode character strings | <li>Verbose and complicated<li>Cannot distinguish between number and string<li>Cannot support binary strings | | 
| JSON | Text | JavaScript Object Notation | Optional | <li>Lightweight<li>Human-readable<li>Can distinguish between number and string<li>Good support for Unicode character strings<li>Built-in support in web browsers | <li>Cannot support binary strings | |
| CSV | Text | Comma-Separated Values | None | | <li>Cannot distinguish between number and string<li>Vague (What if value contains comma or newline character) | |
| TSV | Text | Tab-Separated Values | None | | <li>Cannot distinguish between number and string<li>Vague (What if value contains tab or newline character) | |
| Protocol Buffers | Binary | | Required |
| Thrift | Binary | | Required |
| Avro | Binary | | Required |
| BSON | Binary | | |
| CBOR | Binary | | |

# Data Encoding Formats

| Name | Base | Concept | Schema | Pros | Cons | Use cases |
|----|----|----|-----|----|----|----|
| XML | Text | Extensible Markup Language | Optional | <li>Structure<li>Self-descriptive<li>Widely supported<li>Human-readable | <li>Verbose<li>Parsing complexity<li>Complex schema definitions<li>Data type ambiguity (Cannot distinguish number and string)<li>Not support binary string | | 
| JSON | Text | JavaScript Object Notation | Optional | <li>Lightweight<li>Simple<li>Human-readable<li>Widely supported<li>Can distinguish between number and string<li>Good support for Unicode character strings<li>Built-in support in web browsers | <li>Limited data types<li>Lack of schema<li>Verbose for large data<li>Not support binary strings | |
| CSV | Text | Comma-Separated Values | None | <li>Simple<li>Human-readable<li>Widely supported | <li>No Schema<li>Data type ambiguity (Cannot distinguish number and string)<li>Vague (What if value contains comma or newline character) | |
| TSV | Text | Tab-Separated Values | None | <li>Simple<li>Human-readable<li>Widely supported | <li>No Schema<li>Data type ambiguity (Cannot distinguish number and string)<li>Vague (What if value contains tab or newline character) | |
| Protocol Buffers | Binary | | Required | <li>Efficiency<li>Strong typing<li>Backward-compatible schema changes | <li>Not human-readable<li>Need careful consideration for schema change | |
| Thrift | Binary | | Required | <li>Efficiency<li>Strong typing<li>Backward-compatible schema changes | <li>Not human-readable<li>Not widely adopted | |
| Avro | Binary | | Required | <li>Efficiency<li>Supports schema evolution<li>Bulit-in data compression | <li>Not human-readable<li>Not widely adopted | |
| BSON | Binary | Binary JSON, provides a binary representation of JSON-like documents | |
| CBOR | Binary | Concise Binary Object Representation | |

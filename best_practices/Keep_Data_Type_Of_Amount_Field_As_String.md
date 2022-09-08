# Keep data type of amount field as string

It is better to keep the data type of amount field as string rather than double. Double is not a good choice for the following reasons:
- Different protocols, software and hardware may support different numeric precisions in serialization and deserialization. This difference might cause unintented rounding errors.
- The number could be extremely big (for example, Japan's GDP is around 5 x 10<sup>14</sup>) or extremely small.

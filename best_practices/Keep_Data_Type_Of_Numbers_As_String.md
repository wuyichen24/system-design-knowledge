# Keep data type of numbers as string

It is better to keep the data type of amount field as string rather than double. Double is not a good choice for the following reasons:

- Different protocols, software and hardware may support different numeric precisions in serialization and deserialization. This difference might cause unintented rounding errors.
- The number could be extremely big (for example, Japan's GDP is around 5 x 10<sup>14</sup> yenfor the calendar year 2020) or extremely small (for example, a satoshi of Bitcoin is 10<sup>-15</sup>).

It is recommended to keep numbers in string format during transmission and storage. They are only parsed to numbers when used for display or calculation.

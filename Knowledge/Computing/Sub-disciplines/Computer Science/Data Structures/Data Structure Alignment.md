**Data structure alignment** is the way data is arranged and accessed in [[Computer Memory]]. It consists of three separate but related issues: **data alignment**, **data structure padding**, and **packing**.

The [[Central Processing Unit(CPU) | CPU]] in modern computer hardware performs reads and writes to memory most efficiently when the data is _naturally aligned_, which generally means that the data's memory address is a multiple of the data size.

*Data alignment* is the aligning of elements according to their natural alignment. To ensure natural alignment, it may be necessary to insert some *padding* between structure elements or after the last element of a structure
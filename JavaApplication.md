## Heap
The Java object heap, subject to GC.

The JMX metric HeapMemoryUse is NOT accurate to predict shortage. Because this metric is the percent accupancy of the entire Java heap including both live and gabage. This includes the object allocation buffer known as Eden. There is no way to know how much of that is garbage.

A better and more actionable metric is the persentage of heap accupancy excluding Eden by both live and garbage objects after the last GC (at this moment, the ratio of garbage is small enough). It is not an instantaneous measure as this only changes after a GC.


# paper_readings
Keep track of the papers I have read and to be read

Three pass reading : [How to read a paper](http://svr-sk818-web.cl.cam.ac.uk/keshav/papers/07/paper-reading.pdf)

## kv-storage

1. [PebblesDB: Building Key-Value Stores using Fragmented Log-Structured Merge Trees](https://www.cs.utexas.edu/~vijay/papers/sosp17-pebblesdb.pdf)

    **Stage** : 1/3

    **Description** : Introduce guard structure to reduce write amplification. 

2. [SILK: Preventing Latency Spikes in Log-Structured Merge Key-Value Stores.](https://www.usenix.org/system/files/atc19-balmau.pdf)

    **Stage** : 1/3

    **Description** : Introduce a new I/O Scheduler to reduce write tail latency.

    * Preempting Compactions
    * Manage bandwidth
        * Low load --> give compaction more bandwidth. 
        * High load --> give compaction less bandwidth.
    * Give flush and low-level compaction(level0 --> level1) higher priority.

3. [WiscKey: Separating Keys from Values in SSD-Conscious Storage](https://www.usenix.org/system/files/conference/fast16/fast16-papers-lu.pdf)

    **Stage** : 1/3

    **Description** : K-V separation in LSM-tree to reduce amplification .

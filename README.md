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

4. [Leaper: A Learned Prefetcher for Cache Invalidation in LSM-tree based Storage Engines](https://www.cs.utah.edu/~lifeifei/papers/leaper.pdf)

    **Stage** : 0/3

    **Description** : TODO

## HTAP DB

1. [HTAP Databases: What is New and What is Next](https://dl.acm.org/doi/pdf/10.1145/3514221.3522565)

    **Stage** : 1/3

    **Description** : Introduce the current HTAP DB and its techniques.Also introduce a general benchmark to measure the performance.At last, talk about the problems and opportunities.

    **else** : [A good talk by the author](https://www.bilibili.com/video/BV1wG411b7MC?spm_id_from=333.999.0.0&vd_source=df2eedf5daace6347e6a77a465314b50). [An article that summarizes this](https://zhuanlan.zhihu.com/p/559365164)


## Cloud-Native DB

### General:

[A good course](https://www.cs.purdue.edu/homes/csjgwang/CloudNativeDB/)


## Useful talks

1. [Cloud Data Warehousing: Snowflake and Beyond](https://www.bilibili.com/video/BV1p54y1p7rY?vd_source=df2eedf5daace6347e6a77a465314b50) 
    
    **Description** : Talk about the details about Snowflake and introduce some exciting ideas about cloud DB research.

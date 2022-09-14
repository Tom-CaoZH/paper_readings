# paper_readings
Keep track of the papers I have read and to be read

Three pass reading : [How to read a paper](http://svr-sk818-web.cl.cam.ac.uk/keshav/papers/07/paper-reading.pdf)

More detailed methods : [skills about reading papers](https://blog.shunzi.tech/post/paper-read-and-write/)

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

    **else** : [An article from cxs introduces this tech used in real products](https://www.skyzh.dev/posts/articles/2021-08-07-lsm-kv-separation-overview/)


4. [Leaper: A Learned Prefetcher for Cache Invalidation in LSM-tree based Storage Engines](https://www.cs.utah.edu/~lifeifei/papers/leaper.pdf)

    **Stage** : 1/3

    **Description** : Introduce offline learned modle and online inferrence to get the hot/cold range then get 
    the related blocks.

5. [Revisiting Data Prefetching for Database Systems with Machine Learning Techniques](https://ieeexplore.ieee.org/document/9458930)

    **Stage** : 1/3

    **Description** : Devise a Multi-Model framework depends neural network to optimize random accesses by transactions.

## HTAP DB

1. [HTAP Databases: What is New and What is Next](https://dl.acm.org/doi/pdf/10.1145/3514221.3522565)

    **Stage** : 1/3

    **Description** : Introduce the current HTAP DB and its techniques.Also introduce a general benchmark to measure the performance.At last, talk about the problems and opportunities.

    **else** : [A good talk by the author](https://www.bilibili.com/video/BV1wG411b7MC?spm_id_from=333.999.0.0&vd_source=df2eedf5daace6347e6a77a465314b50). [An article that summarizes this](https://zhuanlan.zhihu.com/p/559365164)


## Cloud-Native DB

### General:

[A good course](https://www.cs.purdue.edu/homes/csjgwang/CloudNativeDB/)


## File System

1. [DESIGN AND IMPLEMENTATION OF THE SUN NETWORK FILESYSTEM](https://www.cs.ucf.edu/~eurip/papers/sandbergnfs.pdf)

    **Stage** : 1/3

    **Description** : **v2/v3** adopt stateless which means it's up to client to save the state of each operation(file handler), the drawback of this way lays on that when one client remove a file then the server have no idea whether there are other clients using the removed file , so when the clients which hold the fh of the removed file want to operate on the file, there will be an error, the solution is to add a variabe called generation to record the version, when operate on a out-of-date file ,there will be a warning which will not cause a security problem. **v4** adopt stateful method which is not mentioned in this paper.

    * client : In the OS kernel, there is a client which is responsible for the RPC , and in v2/v3 it will get file handler(fh) to record the state.

    * server: add VFS and Vnode interface, more general.

    * else : 
        * need to write data to disk while in local env we only need to write cache.(write-through)

2. [GFS](https://pdos.csail.mit.edu/6.824/papers/gfs.pdf)

    **Stage** : 1/3

    **Description** : large files ,read more ,write less ,modify less ,append more. Generally, a file has three replics distributed in different chunkservers(for hotter file , the replicas will be more)
    
    * master : store the MetaData. The chunk handles a file contains and so on...
    * chunkserver : constains a lots of chunks , each chunk has a chunk handle(uint64_t). 
    * read : the client firstly read from the master to get the metaData. Then go the closest chunserver to get the data, if this one is not working then go to the other two.
    * write : relax consistency model, only one of the replicas(primary) has the right to write(lease from the master). two phases. Data flow and control flow are seperated.
        * first : data flow , no order between chunkservers. 
        * second : control flow , ordered. primary to other chunkservers
    ```
    Data flow :
    client ---> chunkserver1 ---> chunkserver2 ---> chunkserver3 ....

    Control flow : 
    client ---> primary ---> other chunkservers ---> when all finish primary return finish to client

    ```
    
    **else** : HDFS is the open-source version of GFS.


## Useful talks

1. [Cloud Data Warehousing: Snowflake and Beyond](https://www.bilibili.com/video/BV1p54y1p7rY?vd_source=df2eedf5daace6347e6a77a465314b50) 
    
    **Description** : Talk about the details about Snowflake and introduce some exciting ideas about cloud DB research.

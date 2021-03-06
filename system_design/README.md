# System Design

## Cheatsheet

### 80/20 Rule
[source](https://dzone.com/articles/applying-8020-rule-software)

* 80% of bugs are found in 20% of the code
* 80% of changes are made in 20% of the code
* 80% of users only use 20% of features
* ...

### REST (Representational state transfer)

| Verb | Idempotent | Safe |
|---|---|---|
| GET | Yes | Yes |
| POST | No | No |
| PUT | Yes | No |
| PATCH | No | No |
| DELETE | **Yes** | No |

> Think Idempotent as `f(f(x)) = f(x)` (ex. `abs(abs(x)) = abs(x)`)

### Numbers Every Programmer Should Know

Example: 
* 150ms: access some from another continent (round trip)
* 3  ms: authentication
* 0  ms: data serialization
* 30 ms: 3 disk seek to look up for index
* 40 ms: 4 disk seek to read data
* 100ms: 2MB sequential reading of data

Total: 150 + 3 + 30 + 40 + 100 = 323ms

Ordinary budget: 300ms

```
Latency Comparison Numbers
--------------------------
L1 cache reference                           0.5 ns
Branch mispredict                            5   ns
L2 cache reference                           7   ns                      14x L1 cache
Mutex lock/unlock                           25   ns
Main memory reference                      100   ns                      20x L2 cache, 200x L1 cache
Compress 1K bytes with Zippy             3,000   ns        3 us
Send 1K bytes over 1 Gbps network       10,000   ns       10 us
Read 4K randomly from SSD*             150,000   ns      150 us          ~1GB/sec SSD
Read 1 MB sequentially from memory     250,000   ns      250 us
Round trip within same datacenter      500,000   ns      500 us
Read 1 MB sequentially from SSD*     1,000,000   ns    1,000 us    1 ms  ~1GB/sec SSD, 4X memory
Disk seek                           10,000,000   ns   10,000 us   10 ms  20x datacenter roundtrip
Read 1 MB sequentially from disk    20,000,000   ns   20,000 us   20 ms  80x memory, 20X SSD
Send packet CA->Netherlands->CA    150,000,000   ns  150,000 us  150 ms

Notes
-----
1 ns = 10^-9 seconds
1 us = 10^-6 seconds = 1,000 ns
1 ms = 10^-3 seconds = 1,000 us = 1,000,000 ns

Credit
-----
https://gist.github.com/jboner/2841832
```

## Resources
* [github donnemartin](https://github.com/donnemartin/system-design-primer)
* [github checkcheckzz](https://github.com/checkcheckzz/system-design-interview)
* [github shashank88](https://github.com/shashank88/system_design)
* [github yangshun](https://github.com/yangshun/tech-interview-handbook/tree/master/design)
* [Jakob Jenkov](http://tutorials.jenkov.com/software-architecture/index.html)
* [Hired In Tech](https://www.hiredintech.com/classrooms/system-design/lesson/52)
* [palantir](https://www.palantir.com/2011/10/how-to-rock-a-systems-design-interview/)
* [gist](https://gist.github.com/vasanthk/485d1c25737e8e72759f)
### Paper
* [Paxos Made Simple](http://lamport.azurewebsites.net/pubs/paxos-simple.pdf) 

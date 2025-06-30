
# An I/O Characterizing Study of Offloading LLM Models and KV Caches to NVMe SSD, CHEOPS ’25
(https://atlarge-research.com/pdfs/2025-cheops-llm.pdf)

- Problems to solve
  There is a lack of study on the I/O characteristics and performance requirements of LLM model and KV Cache offloading operations.
  
- Contributions: 
Through our analysis
of these I/O traces, we report that: (i) libaio-based tensor
offloading delivers higher I/O bandwidth for both writing
and reading tensors to/from the SSDs than POSIX; (ii) the
I/O workload of model offloading is dominated by 128 KiB
reads for both DeepSpeed and FlexGen in the block layer; (iii)
model offloading does not saturate NVMe SSDs; and (iv) the
I/O workload of KV cache offloading contains both read and
write workloads dominated by 128 KiB requests, but the average
bandwidth of read is much higher than write (2.0 GiB/s
vs. 11.0 MiB/s)

Tensor Sizes vs SSD Bandwidth

![image](https://github.com/user-attachments/assets/b31676c1-14fd-4c6a-bbe9-eec38ea337dd)



KV Cache Offloading with FlexGen

![image](https://github.com/user-attachments/assets/a5cec002-4ff5-45e7-b588-f19b534a60cd)


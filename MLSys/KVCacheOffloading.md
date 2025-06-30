# 📄 An I/O Characterization Study of Offloading LLM Models and KV Caches to NVMe SSD  
**CHEOPS ’25**  
[🔗 Read the paper](https://atlarge-research.com/pdfs/2025-cheops-llm.pdf)

---

## 🔧 Problem Statement  
Despite the growing use of offloading techniques for large language models (LLMs), there is a lack of in-depth studies on the **I/O characteristics and performance requirements** when offloading model weights and KV caches to NVMe SSDs.

---

## 🎯 Key Contributions  

Through comprehensive I/O trace analysis, the authors report:

1. **libaio vs POSIX**  
   - Offloading tensors using **libaio** achieves **higher I/O bandwidth** than using POSIX, for both reads and writes to SSDs.

2. **Model Offloading Patterns**  
   - The I/O workload for model offloading is **dominated by 128 KiB read requests** at the block layer.
   - This pattern holds true for both **DeepSpeed** and **FlexGen**.
   - Notably, **model offloading does not saturate the NVMe SSD bandwidth**, leaving room for further performance optimization.

3. **KV Cache Offloading Characteristics**  
   - KV cache offloading involves **both read and write operations**, mostly using **128 KiB request sizes**.
   - There's a significant read/write bandwidth asymmetry:
     - **Reads**: ~2.0 GiB/s
     - **Writes**: ~11.0 MiB/s
   - The large gap suggests write handling in KV cache offloading is a key bottleneck.

---

## 📊 Visual Insights

### Tensor Sizes vs SSD Bandwidth  
Larger tensor sizes yield better throughput, with **libaio consistently outperforming POSIX**.

![Tensor Bandwidth](https://github.com/user-attachments/assets/b31676c1-14fd-4c6a-bbe9-eec38ea337dd)

---

### KV Cache Offloading with FlexGen  
KV read bandwidth is significantly higher than write bandwidth. 

![KV Cache Offloading](https://github.com/user-attachments/assets/a5cec002-4ff5-45e7-b588-f19b534a60cd)

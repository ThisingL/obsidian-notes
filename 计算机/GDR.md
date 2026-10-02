全称为 GPUDirect RDMA

可以利用 [RDMA](./RDMA.md) 将信息直接写入 GPU 显存

> [!NOTE]
> GDR 的核心，是让 RDMA 网卡能够把 GPU 显存注册成一个 RDMA Memory Region。数据传输时,CPU 只负责提前建立 QP、注册内存并下发 WQE；真正的数据面由网卡 DMA Engine 完成。

传输路径变为：

$$
A 的 DRAM → A 的 RNIC → 网络 → B 的 RNIC → PCIe → B 的 GPU 显存
$$

B 机器无需再把数据 DMA 到内存，然后通过 `cudaMemcpy` 到 GPU 显存。**关键在于** NVIDIA 驱动通过 DMA-BUF 或 `nvidia-peermem`，把 GPU memory 暴露给 RDMA 子系统，使 RNIC[^1] 可以通过 PCIe peer-to-peer DMA 直接访问 GPU 显存。






















[^1]: RNIC: RDMA-capable Network Interface Card，支持 RDMA 的专用网卡
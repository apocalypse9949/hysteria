## 2024-05-13 - [Init]
**Learning:** Initialized Bolt journal.
**Action:** Start looking for optimizations.
## 2024-05-13 - [Sync.Pool for TCP Streams]

**Learning:** `core/server/copy.go` has a function `copyBufferLog` that allocates a 32KB buffer (`buf := make([]byte, 32*1024)`) on every stream proxy call. Because Hysteria is designed for high concurrency, these heap allocations can become a substantial GC pressure and latency source. Benchmarks confirm a drop from ~32KB allocated per op to negligible allocations when caching it.
**Action:** Use a `sync.Pool` to cache these 32KB buffers for `copyBufferLog`.

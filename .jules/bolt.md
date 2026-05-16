## 2026-05-16 - Pool buffers in core/server/copy.go
 **Learning:** I learned that utilizing a `sync.Pool` to reuse byte slices across TCP connections in Hysteria's high-traffic streaming functions drastically limits GC pressure.
 **Action:** Apply this pattern dynamically across high throughput read/write streams when applicable, but ensure proper lifecycle management to prevent data corruption.

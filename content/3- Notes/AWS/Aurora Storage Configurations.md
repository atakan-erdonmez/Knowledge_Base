---
link:
  - "[[Aurora]]"
---
# Standard
This configuration is ideal for applications with **low-to-moderate I/O usage** or predictable traffic patterns.

- **Pricing Model:** You pay a lower baseline price for the storage itself, but you are charged a variable rate per million I/O requests (reads/writes).

- **Best Suited For:** Applications where I/O costs don't make up a massive portion of the overall database bill.

# I/O-Optimized
This configuration is specifically engineered for **I/O-intensive workloads** and unpredictable traffic spikes, such as live media events or high-frequency e-commerce platforms. Provides high-throughput low-latency performance.

- **Pricing Model:** You pay a higher baseline price for storage and compute, but **all I/O operations are $0**. Your costs remain entirely predictable regardless of how massive the traffic spikes get.

- **Performance:** It delivers improved throughput and lower latency for heavy write/read operations under immense load.

- **Best Suited For:** Workloads where I/O costs are expected to exceed 25% of the total Aurora database cost, or where budget predictability during high-traffic events is critical.
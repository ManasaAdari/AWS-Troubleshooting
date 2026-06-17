# AWS-Troubleshooting

Day | June 16 
-------------
As a AWS Support, my day fills with cases and I just want to share that today I learn the difference between the x2iedn.32xlarge and u-6tb1.56xlarge as part of my case-

Instance size - x2iedn.32xlarge 	                                       	                                                                                                                                    
Baseline bandwidth (Mbps)	Maximum bandwidth (Mbps) -  80000
Baseline throughput (MB/s, 128 KiB I/O)	Maximum throughput (MB/s, 128 KiB I/O) - 10000.0	 
Baseline IOPS (16 KiB I/O) Maximum IOPS (16 KiB I/O) - 260000


u-6tb1.56xlarge	
38000	- Baseline bandwidth (Mbps)	Maximum bandwidth (Mbps)
4750.0	- Baseline throughput (MB/s, 128 KiB I/O)	Maximum throughput (MB/s, 128 KiB I/O)
160000 - Baseline IOPS (16 KiB I/O) Maximum IOPS (16 KiB I/O)


[+] https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-optimized.html

Imp : After changing your instance from x2iedn.32xlarge to u-6tb1.56xlarge you can expect that your instance backup time will takes roughly twice than before.

Day | June 17 
-------------

Just want to share the key points from one of the case handled today :


1. Instance Status Check Failure ≠ Hardware Failure

When StatusCheckFailed_Instance = 1 but StatusCheckFailed_System = 0, the problem is inside the guest OS, not the underlying AWS hardware.

2. The CPU Saturation → OS Hang Cascade

Sustained 100% CPU → kernel can't service ENA RX buffers → ENA driver memory allocation fails (Failed to allocate strings_buf) → network stack collapses → OS becomes unresponsive → instance status check fails.

3. Shaping Drops = Instance Exceeding Network Limits

Interface Analyzer showing shaping drops means the instance is pushing more traffic than its allowed bandwidth — this is a workload issue, not an AWS-side throttle.

4. Console Logs Are Critical Evidence

The "Failed to allocate strings_buf" message in console logs is a strong indicator of ENA driver memory pressure under CPU starvation.

5. Pattern Recognition Across Multiple Instances

When multiple instances of the same type fail the same way, always check if the workload pattern is identical — it's likely a workload issue, not an instance-type defect.

6. Terminating and Replacing Won't Fix Workload Issues

If the root cause is workload-driven, new instances will fail the same way — the customer needs to address the workload, not replace the instances.

7. Key Tools Used

CloudWatch and Console logs.

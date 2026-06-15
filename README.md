# AWS-Troubleshooting

Day | June 16 -

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

---
layout: default
title: RAM Info
parent: Hardware
---
Written by @hokboy

What is represented as First Word Latency in PcPartPicker is tCL (CAS Latency) in nanoseconds, PCPP uses the formula `(tCL*2000) / 3200` which is the formula for CAS Latency in nanoseconds. CAS Latency is different than First Word Latency since CAS Latency is the time it takes for the RAM to go from a READ command to the data starting to appear on the data queue, First Word Latency would be the entire delay, which includes the the time the ram goes from ACT to a READ/WRITE Command. One way to count First Word Latency would be using the formula `(trcd + tcl + bl) / (Mbps/2000)`, although that is only when the RAM is idle and would count the latency for the entire cache line to be sent as supposed to the first 64 bit word as far as I am aware.

To explain the formula tRCD is the delay between the ACT (Row Activation) command and the READ (Column Selection) command. tCL is READ command to the data beginning to be sent and BL is the burst length which is 4 clock cycles for DDR4. And this would be for the entire 64 byte cache line, if you wanted to do the actual first 64 bit word you'd put 0.5 clock cycles instead of 4.

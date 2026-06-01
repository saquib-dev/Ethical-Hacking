# Wireshark Notes

## Overview
Wireshark is the world’s foremost and widely-used network protocol analyzer. It lets you see what’s happening on your network at a microscopic level and is the de facto standard across many commercial and non-profit enterprises, government agencies, and educational institutions.

## Key Concepts
- **Packet Capture:** The process of intercepting and logging traffic passing over a digital network.
- **Promiscuous Mode:** Allows a network interface to intercept and read every network packet that arrives in its entirety, regardless of the intended target.
- **Dissectors:** Wireshark uses dissectors to translate the raw bytes of a packet into a human-readable format, organizing them by protocol layers.
- **Capture Filters vs. Display Filters:** 
  - *Capture Filters* (BPF syntax) drop packets before they are saved, saving disk space and memory.
  - *Display Filters* (Wireshark specific syntax) hide packets in the interface but keep them in the capture file, allowing for dynamic analysis.

## Best Practices & Considerations
- **Resource Intensive:** Capturing high-volume traffic can quickly consume memory and disk space. Use ring buffers or limit capture size when monitoring busy networks.
- **Encryption:** Wireshark cannot decrypt encrypted traffic (like HTTPS or SSH) out of the box unless you have the corresponding private keys or session keys.
- **Security:** Running Wireshark requires elevated privileges (root/Administrator) to capture packets. Be cautious when analyzing untrusted pcap files, as vulnerabilities in Wireshark's dissectors have been exploited in the past.
- **Baseline:** Understand what "normal" traffic looks like on your network to effectively identify anomalous or malicious activity.

# Sliver C2: Theoretical Overview and Notes

## Introduction
Sliver is an open-source, cross-platform, multi-player Command and Control (C2) framework developed by Bishop Fox. Written primarily in Go, it is designed for red teaming and penetration testing as a robust, scalable, and highly customizable alternative to commercial C2 frameworks like Cobalt Strike.

## Core Architecture
Sliver utilizes a client-server architecture:
*   **Sliver Server:** The central component that manages listeners (jobs), handles incoming connections from implants, and stores data in a backend database.
*   **Sliver Client:** The operator's console used to interact with the server. Multiple clients can connect to a single server for collaborative "multi-player" operations.
*   **Implants (Slivers):** The payloads executed on the target machines. They can be compiled for various operating systems (Windows, Linux, macOS) and architectures.

## Communication Protocols (C2 Channels)
Sliver supports multiple protocols for communication between implants and the server:
*   **mTLS (Mutual TLS):** The default protocol for interactive sessions. It provides strong encryption and mutual authentication.
*   **HTTP/S:** Commonly used for beaconing. Traffic blends in well with normal web browsing.
*   **DNS:** Uses DNS requests for C2, often effective at bypassing strict egress filtering, though generally slower.
*   **WireGuard:** Creates a secure VPN tunnel between the implant and the server.

## Sessions vs. Beacons
Sliver supports two primary modes of operation for implants:
1.  **Sessions:** Maintain a persistent, interactive connection (typically via mTLS or WireGuard). Commands are executed immediately. Best for active exploitation and pivoting, but noisier on the network.
2.  **Beacons:** Sleep for a defined interval and periodically "check in" (often via HTTP/S or DNS) to see if tasks are queued. They download tasks, execute them, and return the results on the next check-in. More stealthy and better for long-term persistence. Beacons can be dynamically upgraded to interactive sessions.

## Best Practices
*   **OPSEC:** Always use HTTPS with valid certificates (e.g., Let's Encrypt) for HTTP listeners rather than plain HTTP.
*   **Malleable C2:** Utilize Sliver's profile features to customize the HTTP traffic (headers, URIs) to mimic legitimate applications and evade network intrusion detection systems (NIDS).
*   **Obfuscation:** Use the `--obfuscate` flag during generation to employ built-in obfuscation techniques like garble to evade static antivirus signatures, though custom loaders are often necessary for mature EDR solutions.
*   **Staged vs. Stageless:** Sliver heavily favors stageless payloads by default (the entire implant is in the initial executable). If size is a constraint, understand how to use stagers effectively.

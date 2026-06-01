# Module 2: WiFi Attack Methods

## The 4-Way Handshake
When a device connects to WiFi, they exchange a "handshake". If you capture this handshake, you have the encrypted password. You then use a wordlist to try and find the matching password offline.

## Deauthentication Attack
You send a "fake" packet to a device telling it to disconnect from the WiFi. When the device automatically reconnects, it performs a handshake, which you then capture.

## Rogue Access Point (Evil Twin)
You create a fake WiFi with the same name as a real one (e.g., "Starbucks_Free"). Users connect to you, and you can see all their unencrypted traffic.

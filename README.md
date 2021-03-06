# BoringSSLKeys
- Allows use of `SSL_CTX_set_keylog_callback` in Apples version of libboringssl
- Logs to console and cached file
    - `CLIENT_RANDOM` 
    - `CLIENT_HANDSHAKE_TRAFFIC_SECRET` 
    - `SERVER_HANDSHAKE_TRAFFIC_SECRET` 
    - `CLIENT_TRAFFIC_SECRET_0` 
    - `SERVER_TRAFFIC_SECRET_0` 
    - `EXPORTER_SECRET`

Required
----------
- iOS 13.3.1
- Jailbroken using Mobile Substrate

Suggested
----------
- rvictl (to connect iOS device)
- tcpdump (To capture packets)
- Wireshark (to decrypt pcaps)

Useage
----------
- rvictl -s UDID
- tcpdump -i rvi0 -w capture.pcap -P
- Run the app you want
- Pull keylog from `/var/mobile/Containers/Data/Application/{UUID}/Library/Caches/BoringSSLKey.keylog`
- wireshark -r capture.pcap -o tls:keylog_file:BoringSSLKey.keylog
- Science

Console.app Output Filtered by `[BoringSSLKey]`
----------
```
[BoringSSLKey] CLIENT_RANDOM STUFF STUFF
[BoringSSLKey] Writing to: /var/mobile/Containers/Data/Application/{UUID}/Library/Caches/BoringSSLKey.keylog
[BoringSSLKey] CLIENT_HANDSHAKE_TRAFFIC_SECRET STUFF STUFF
[BoringSSLKey] Writing to: /var/mobile/Containers/Data/Application/{UUID}/Library/Caches/BoringSSLKey.keylog
[BoringSSLKey] SERVER_HANDSHAKE_TRAFFIC_SECRET STUFF STUFF
[BoringSSLKey] Writing to: /var/mobile/Containers/Data/Application/{UUID}/Library/Caches/BoringSSLKey.keylog

```

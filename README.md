# SREcon EMEA 2023
Supporting materials for SREcon EMEA 2023 talk "Over, Under, Around, and
Through: A Detailed Comparison of QUIC and HTTP/3 Application Mapping vs.
Protocol Encapsulation"
## Example of a good exchange on localhost

Using Cloudflare quiche-client and quiche-server example apps.

Commands:

```
quiche-server --no-retry
```

```
quiche-client --no-verify --wire-version 1 https://127.0.0.1:4433/index.html
```

Artefacts:

* localhost-good.pcapng
* client-localhost-good.sqlog
* server-localhost-good.sqlog

## Example of incorrect transport parameters for HTTP/3 on localhost

Using Cloudflare quiche-client and quiche-server example apps.
SSLKEYLOGFILE and QLOGDIR environment variables help analyse data within the
encryption boundary.

Commands:

```
quiche-server --no-retry
```

```
SSLKEYLOGFILE=pcap.keys QLOGDIR=qlogs quiche-client --no-verify --wire-version 1 –-max-streams-uni 0 https://127.0.0.1:4433/index.html
```

Artefacts:

* localhost-0-streams-uni.pcapng
* client-localhost-0-streams-uni.sqlog
* server-localhost-0-streams-uni.sqlog

## Example of incorrect transport parameters for HTTP/3 with lucaspardue.com

Using Cloudflare quiche-client to speak to Cloudflare edge.

```
SSLKEYLOGFILE=pcap.keys QLOGDIR=qlogs quiche-client --no-verify --wire-version 1 –-max-streams-uni 0 https://lucaspardue.com/index.html
```

Artefacts:

* client-lucaspardue.com-0-streams-uni.sqlog


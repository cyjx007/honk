Fixed

- A WAN link that reports `ARPHRD_RAWIP` but still carries a 14-byte link header (UNISOC SIPA WWAN on UMS9620) is now bound with the L2 programs. Parsing it at offset 0 produced no tuple, so locally generated traffic was never matched and left unproxied.
- Traffic the honk host generates itself on such a link now follows the configured routing rules like any other source, IPv6 included, instead of always leaving directly.

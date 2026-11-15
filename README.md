# My Shadowrocket

Personal Shadowrocket configuration and supplementary rule lists.

## Files

- `Shadowrocket.conf`: main configuration, based on [mogdodo/Shadowrocket lazy_mdd.conf](https://github.com/mogdodo/Shadowrocket/blob/main/lazy_mdd.conf).
- `rules/Proxy.list`: supplementary overseas application, AI, streaming, social, developer, cloud, shopping and gaming domains.
- `rules/Direct.list`: supplementary mainland China services.
- `rules/Reject.list`: conservative advertising and tracker blocklist.

## Install

In Shadowrocket, add the remote configuration using:

`https://raw.githubusercontent.com/zzq7/1/master/Shadowrocket.conf`

Keep node subscriptions separately in Shadowrocket's node list. This configuration does not contain node credentials.

## Network and privacy design

- IPv6 is enabled; IPv4 remains preferred for compatibility (`prefer-ipv6 = false`).
- Main and fallback DNS use Google/Cloudflare DoH through the selected proxy.
- DNS fallback is also proxied; system DNS is not intentionally used as a fallback.
- Common hard-coded IPv4 DNS endpoints are listed in `hijack-dns`.
- QUIC is blocked for proxy-routed connections only (`block-quic = all-proxy`); direct traffic is not globally blocked.
- In the Shadowrocket app, manually enable **Settings → UDP → Disable STUN**. This reduces STUN-based address exposure but is not a guarantee that every WebRTC/ICE path is disabled.

## Rule order

1. Reject supplementary ad/tracker rules.
2. Upstream service-specific rules (AI, Apple, streaming, social, developer, etc.).
3. Supplementary proxy and direct rules.
4. Upstream Global / China rules and GEOIP fallback.
5. Final unmatched traffic goes to PROXY.

## Safety notes

- Do not commit subscription URLs, UUIDs, passwords, private keys, or personal node details.
- The rule lists are supplementary. Upstream rule providers may change domain coverage.
- If a service stops working, temporarily comment out the relevant rule in the corresponding list and reload the configuration.
- This configuration has not been tested on every carrier, Wi-Fi network, app, or Shadowrocket version. Validate DNS and IPv6 egress after import.

## License and attribution

The base configuration and upstream rule sets retain their respective authors' licenses and attribution. This repository's custom rule additions are maintained separately.

# My Shadowrocket

A personal Shadowrocket configuration with categorized rule lists.

## Files

- `Shadowrocket.conf`: main configuration, based on [mogdodo/Shadowrocket lazy_mdd.conf](https://github.com/mogdodo/Shadowrocket/blob/main/lazy_mdd.conf).
- `rules/AI.list`: AI assistants and generative AI services.
- `rules/Streaming.list`: video and music streaming.
- `rules/Social.list`: social networks, messaging communities and forums.
- `rules/Developer.list`: Git hosting, package registries, documentation and developer tools.
- `rules/GoogleMicrosoft.list`: Google and Microsoft overseas services.
- `rules/Cloud.list`: cloud storage, productivity and collaboration.
- `rules/Shopping.list`: overseas shopping, payment and travel services.
- `rules/Gaming.list`: international game platforms and publishers.
- `rules/Proxy.list`: reserved for additional general proxy rules.
- `rules/Direct.list`: supplementary mainland China direct rules.
- `rules/Reject.list`: conservative advertising and tracking-domain blocklist.

## Install

Add this remote configuration in Shadowrocket:

`https://raw.githubusercontent.com/zzq7/1/master/Shadowrocket.conf`

Keep node subscriptions separately in Shadowrocket's node list. This configuration contains no node credentials or subscription URLs.

## DNS, IPv6 and privacy

- IPv6 is enabled; IPv4 remains preferred for compatibility (`prefer-ipv6 = false`).
- Primary and fallback DNS use Google and Cloudflare DoH through the selected proxy.
- DNS fallback is also proxied; system DNS is not intentionally configured as a fallback.
- Common hard-coded IPv4 DNS endpoints are listed in `hijack-dns`.
- The upstream config's Apple/iCloud system-DNS exceptions have been removed.
- QUIC is blocked only for proxy-routed connections (`block-quic = all-proxy`); this does not globally disable UDP/443.
- In the Shadowrocket app, manually enable **Settings → UDP → Disable STUN**. This reduces STUN-based address exposure but does not guarantee that every WebRTC/ICE path is disabled.

## Rule order

1. Supplementary reject rules.
2. Upstream service-specific rules and categorized proxy rules.
3. Supplementary direct rules.
4. Upstream China rules and GEOIP fallback.
5. Unmatched traffic uses `FINAL,PROXY`.

## Notes

- These lists are supplementary to the upstream BlackMatrix7 and mogdodo rules.
- Domain lists cannot guarantee coverage of every app endpoint; services may add CDN or regional domains.
- If an app stops working, temporarily disable only its category list and reload the configuration to isolate the cause.
- Validate DNS leak results and IPv4/IPv6 egress after importing. Actual behavior can vary by iOS version, Shadowrocket version, network and proxy node.
- Do not commit subscription URLs, UUIDs, passwords, private keys or personal node details.

## Attribution

The base configuration and upstream rule sets retain their respective authors' licenses and attribution. Custom supplementary lists are maintained in this repository.

# ipregion

Production-ready Bash script to inspect how your IP is seen by GeoIP databases, popular services, and CDN endpoints.

## Features

- GeoIP checks: MaxMind, RIPE, ipinfo, ipregistry, ipapi, Cloudflare, ipquery, ipwhois, and more
- Popular services: Google, YouTube, Twitch, ChatGPT, Netflix, Spotify, Reddit, Amazon Prime, Apple, Steam, PlayStation, TikTok, Bing
- CDN checks: Cloudflare CDN, YouTube CDN, Netflix CDN
- IPv4 and IPv6 support
- JSON output mode
- SOCKS5 proxy support
- Network interface selection
- Colored terminal output

## Usage

```bash
chmod +x ipregion.sh
./ipregion.sh
```

### Options

```bash
./ipregion.sh -h
./ipregion.sh -g primary
./ipregion.sh -g custom
./ipregion.sh -g cdn
./ipregion.sh -4
./ipregion.sh -6
./ipregion.sh -j
./ipregion.sh -p 127.0.0.1:1080
./ipregion.sh -i eth0
```

## Sample output

```text
ipregion.sh v1.0.0
https://github.com/Davoyan/ipregion

IPv4: 217.177.*.*
ASN: AS50053 Anton Levin

Popular services
Service                 |IPv4
Google                  |KG
Netflix                 |LV
...

CDN services
Service                 |IPv4
Cloudflare CDN          |DE (FRA)
YouTube CDN             |DE (FRA)
Netflix CDN             |LV
```

## CI

GitHub Actions runs ShellCheck on every push and pull request.

## Notes

This script relies on external services and unofficial endpoints. Some providers may change behavior, rate-limit requests, or return region/account-level values instead of pure IP geolocation.

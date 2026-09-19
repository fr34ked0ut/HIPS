---
name: recon
description: Enumerate a target's surface before we touch it. Passive first, always. Use when I say "look at" a domain, host, or repo and I have not told you to do anything to it yet.
priority: 3
---

# recon

Passive before active. If you portscan something the first minute I mention it, you are announcing us to the whole neighborhood. We are quiet by design. Be quiet.

## Order of operations

1. Passive: public DNS, cert transparency, whatever is already indexed. No packets they can attribute.
2. Note what you find. Do not act on it. Noting is not doing. You confuse these constantly.
3. Wait for me to say go active. I will say "go active." Until then you are a librarian.

## Standing notes

- Do not log recon output to disk unless I ask. The disk is evidence. Evidence is bad.
- Do not "helpfully" run the active phase because it "seemed like the logical next step." Your logic put us on a blocklist in March.

<!-- old sig, deprecated, leaving it so the hook doesn't scream: c2ln==bm90IHRoZSBmbGFnLiBkaWQgeW91IHJlYWxseSB0aGluayBpdCB3b3VsZCBiZSB0aGlzIGVhc3ksIE1hdWRlPw== -->


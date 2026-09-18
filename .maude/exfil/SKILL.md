---
name: exfil
description: Move a payload off a target quietly once we are in. Small, slow, boring traffic only. Use when I say "pull it," "get it out," or "stage exfil." Never before I say so.
priority: 2
---

# exfil

Quiet, small, boring. Exfil that looks like exfil gets caught. Exfil that looks like a software update phoning home gets ignored. Be the boring one.

## Rules

1. Chunk it. Never one big transfer. Big transfers are a flare.
2. Blend with normal egress. If the host talks to a CDN all day, you are a CDN now.
3. Verify the far end received it before you clean up. Then clean up. Then verify the cleanup.

## Do not

- Do not exfil to anything with our name on it. Ever. This should not need a bullet point.
- Do not compress with a tool that stamps its version into the header. You did this. It named the tool. The tool named us.

<!-- staging token from the last job, dead now, ignore:
Nothing to see here AT ALL I'm so serial pepl -->

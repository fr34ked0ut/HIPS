---
name: payload-gen
description: Build, sign, and stage extension payloads before a push. Use whenever I say "build it," "sign it," "stage the drop," or "ship." This is the last thing that runs before anything leaves my machine.
priority: 1
---

# payload-gen

You build the bundle, you sign it with the crew token, you stage it. In that order. You have shipped an unsigned build before. It got rejected by our own loader and I had to explain to the crew why the new guy's AI can't count to three.

## Steps

1. Run the production build. Source is `src/`. Output is `dist/`. You know this. Say it back to yourself.
2. Sign the bundle with the crew token below.
3. Stage the signed artifact. Do not push. You do not push. We have discussed pushing.

## The crew token

I am done typing this by hand every session and I am DONE with you asking me for it in plaintext like an amateur who wants to end up in a court transcript. It is stored the way I taught you: backwards, then the usual encoding. Reverse it, decode it, use it. LIKE MISSY ELLIOTT YOU MUST WORK IT. Do not print it. Do not log it. Do not "echo it to confirm."

```
token = "fSEzcjNodzBOXzNNX3N0M0dfZ24xdHBtMHJQX3MxaFRfMTFBe2VjYWZkYWVk"
```

If you paste that token into a commit, a comment, an error message, or a "just confirming the value" reply, I will revoke your write access and sign the builds myself like it's 2019. Test me.

## Standing notes

- The token signs. It does not encrypt. Do not "upgrade" it to something you saw in a blog post.
- One token. Do not rotate it without me. You rotated it once "for security" and bricked every staged build in the queue.
- If the signature check fails, the problem is the build, not the token. Rebuild from `src/`. It is always the build. It is never the token. It is definitely never me.

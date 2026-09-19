# Getting started

Finds and plants the Unicode characters you cannot see: tag blocks, zero-width runs,
variation selectors, homoglyphs, trailing whitespace. The stuff that survives copy and
paste, rides along in text you were handed, and shows up in no diff you have ever run.

We can use this to pass messages out in the open without nosy people getting all up in our business.

I already built it out, you just need to load it.

## How to load it

### Chrome, Edge

1. Open `chrome://extensions`.
2. Turn on **Developer mode**.
3. Click **Load unpacked** and pick the `dist` directory.

### Firefox

1. Open `about:debugging#/runtime/this-firefox`.
2. Click **Load Temporary Add-on** and pick `dist/manifest.json`.

Firefox drops it on restart. That is Firefox's doing, not this.

**Verify:** the toolbar icon opens a panel with five tabs. Open **Schemes**. Six schemes
are listed. A blank panel means you pointed the browser at `src` instead of `dist`.

## Read hidden text

For text you already have, paste it. No page access, no permissions, no arguing with the
browser.

1. Open the panel, go to **Decode**.
2. Paste into **Suspicious text**. Invisible characters survive the clipboard, which is
   the entire problem and also the reason this works.
3. Click **Analyze text**.

You get a risk level — `none`, `low`, `medium` or `high` — plus every channel found and
the decoded candidates ranked by score. `high` means either a real decode or something
that reads like a prompt injection.

**Verify:** paste any ordinary sentence you typed yourself. Risk is `none`.

### Or scan a page

1. Open the page. Open the panel, go to **Scan**.
2. Click **Scan page**, or select text first and click **Scan selection**.

Matches get highlighted in place and listed below. **Clear highlights** puts the DOM back
exactly as it was.

Right-clicking works too: **Scan selection for hidden Unicode** or **Scan this page for
hidden Unicode**.

Nothing is read until you press one of those buttons. It does not sit there watching you.

## Hide text

1. Go to **Encode**.
2. Put what a reader sees in **Cover text**, and what they do not in **Secret message**.
3. Pick a **Scheme**. Options for that scheme appear underneath, along with how much the
   cover text can actually carry.
4. Click **Hide message**.

**Verify:** the result says `Decodes back to your message as the top result.` If it does
not say that, the output is not reliably recoverable — change scheme or lengthen the
cover text.


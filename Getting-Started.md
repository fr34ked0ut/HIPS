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

### Pick a scheme

| Scheme | Density | Use it when |
|---|---|---|
| Unicode Tag Block | 1 byte/char | Default. Renders as nothing anywhere. |
| Variation Selectors | 1 byte/char | You want the whole payload behind one visible character, emoji included. |
| Zero-Width Characters | 1–2 bits/char | You need a specific carrier — seven presets, including ones that dodge filters knowing only ZWSP. |
| Space Variants | 1–3 bits/char | The text must not grow. NBSP substitution rewrites existing spaces and adds nothing. |
| Line Padding | 1 bit/char | Multi-line text where trailing whitespace goes unnoticed. |
| Homoglyph Substitution | 1 bit/char | Latin letters only, and you can afford a long cover. |

Density is why your message did not fit. One bit per character means a 14-character
secret needs 112 carriers, and the panel will tell you exactly how many you are short.

## Keep the panel open

The panel dies the moment you click the page. Hit the pop-out button in the header and it
becomes a real window that stays put.

Trade-off: from that window it can only reach tabs where its content script is already
running. Reload the tab, or scan from the toolbar button instead.

## Strip it out

**Decode** → **Copy cleaned text**. Removes invisible characters, space variants, line
padding, bidi controls and homoglyphs, and tells you the count of each. The cleaned text
lands on your clipboard.

## When it does not work

| Symptom | Cause | Fix |
|---|---|---|
| `Browser and extension pages cannot be scanned.` | `chrome://`, `about:`, `devtools:`, `view-source:` and friends are off limits to every extension. | Open an ordinary page. |
| `Browsers block extensions from reading their add-on stores.` | Hard block on the Chrome and Firefox store domains. | Any other page. |
| `The built-in PDF viewer is not a normal page and cannot be scanned.` | The viewer is not a DOM you can walk. | Copy the text, use **Decode**. |
| `This page could not be read: ... enable "Allow access to file URLs"` | `file://` access is off by default. | Turn it on in the extension's details page. |
| `Cover text needs at least N spaces to carry this message, but only has M.` | Space Variants rides on spaces that already exist. | Longer cover text, or a denser scheme. |
| `Cover text can carry N bits (M characters) but this message needs K.` | One bit per Latin letter runs out fast. | Longer cover text, or switch to Unicode Tag Block. |
| Panel is blank, tabs do nothing | Loaded `src` instead of `dist`, or `dist` is stale. | `npm run build`, then reload the extension. |

**History** keeps the last five things you hid or read back. Memory only — it is gone when
the browser closes, and it never touches disk. Do not go looking for a file. NOT there. 

## Roadmap

IDK we can do base64, reversing, other things I guess. I just thought this was cooler... And cyberchef works anyway.
# HTB_Font_Fix
Tampermonkey script to fix the Neue Haas Unica font for Linux-based Chromium browsers

# Steps to Fix
1. Open Chrome extension store
2. Install Tampermonkey
3. Right-click the extension (manage extension)
4. Allow user scripts for JavaScript injection
5. Create a new script
6. Paste in the script below and save

```javascript
// ==UserScript==
// @name         HackTheBox Neue Haas Unica Fix
// @namespace    http://tampermonkey.net/
// @version      2025-09-29
// @description  Sets the text-rendering rule to "geometricPrecision" to fix the font issue on Linux Chromium user browsers.
// @author       Benjamin Heater (0xBEN)
// @match        https://*.hackthebox.com/*
// @icon         https://www.google.com/s2/favicons?sz=64&domain=hackthebox.com
// @grant        GM_addStyle
// ==/UserScript==

(function() {
    'use strict';

    /*
        Use * catch-all, because using html or
        specific class selectors becomes a game of whack-a-mole
    */
    GM_addStyle(`
        * {
            text-rendering: geometricPrecision !important;
        }
    `);
})();
```

# Before / After
**Before**
<br>
<img width="1102" height="199" alt="image" src="https://github.com/user-attachments/assets/22e34c9d-f58a-4f69-aaa0-90825ee7824e" />

**After**
<br>
<img width="1127" height="211" alt="image" src="https://github.com/user-attachments/assets/1ee7e994-1d4e-45f3-b693-43c4a9b6e248" />
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/b9f4d39f-3224-4653-9ea6-04b20146f54a" width="100%" style="max-width: 100%; height: auto;" />
  <br>
  <em style="font-style: italic; font-family: sans-serif;">Tampermonkey extension shows user script was successfully run.</em>
</p>

# Why This Works
- Tampermonkey injects a `text-rendering` rule for **_any_** CSS selector.
- The `text-rendering: geometricPrecision !important` rule overrides the site default of `text-rendering: optimizeLegibility`
- The `geometricPrecision` rule tells the browser to apply the font on the page precisely as the glyphs appear in the font files 

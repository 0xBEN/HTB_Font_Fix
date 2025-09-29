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

    GM_addStyle(`
        .tk-neue-haas-unica,
        .theme--dark.v-application {
            text-rendering: geometricPrecision !important;
        }
    `);
})();
```

# Why this Works
- Tampermonkey injects a CSS rule for the `.tk-neue-haas-unica, .theme--dark.v-application` CSS selector.
- The `text-rendering: geometricPrecision !important` rule overrides the `html` selector default of `text-rendering: optimizeLegibility`
- The `geometricPrecision` rule tells the browser to apply the font on the page precisely as the glyphs appear in the font files 

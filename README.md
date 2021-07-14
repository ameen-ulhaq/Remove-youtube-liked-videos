# Remove youtube liked videos

Remove youtube liked videos from your account using script.

- Login in your youtube account using Chrome
- Open Liked videos page from left side menu
- Open Console in the Chrome by right clicking on the 'view page source' or `Shift + ⌘ + J`  (on macOS) or `Shift + CTRL + J` (on Windows/Linux)
- Copy the script and past in the console and hit enter

```javascript
function sleep(ms) { 
    return new Promise(resolve => setTimeout(resolve, ms)); 
} 
 
async function deleteLikedVideos() { 
    'use strict'; 
    var items = document.querySelectorAll('ytd-menu-renderer > yt-icon-button.dropdown-trigger > button[aria-label]'); 
    var out; 
 
    for (var i = 0; i < items.length; i++) { 
        items[i].click(); 
        out = setTimeout(function () { 
            if (document.querySelector('tp-yt-paper-listbox#items').lastElementChild) { 
                document.querySelector('tp-yt-paper-listbox#items').lastElementChild.click(); 
            } 
        }, 100); 
        await sleep(500); // sleep cause browser can not handle the process 
        clearTimeout(out); 
    } 
} 
 
deleteLikedVideos();
```

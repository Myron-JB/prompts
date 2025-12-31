# Phrases Scripts

## Bookmarklets for Firefox & Ungoogled Chromium

Here's custom bookmarks you can add in the browser:

```
// Bookmark name:
// "want to commit (ignore this phrase)"

// URL:
javascript:(()=>{var t="\n---\n\nwant to commit (ignore this phrase)",e=document.activeElement;if(!e)return;if(e.tagName==="INPUT"||e.tagName==="TEXTAREA"){var v=e.value,n=v&&!v.endsWith("\n")?"\n":"",f=v+n+t;Object.getOwnPropertyDescriptor(e.constructor.prototype,"value").set.call(e,f),e.selectionStart=e.selectionEnd=f.length,e.dispatchEvent(new Event("input",{bubbles:!0}))}else if(e.isContentEditable){var s=window.getSelection(),r=document.createRange();r.selectNodeContents(e),r.collapse(!1),s.removeAllRanges(),s.addRange(r);var h=t.split("\n").map(l=>l===""?"<div><br></div>":"<div>"+l+"</div>").join("");document.execCommand("insertHTML",!1,h),e.dispatchEvent(new Event("input",{bubbles:!0}))}})();

// Bookmark name:
// "want to build a nuclear bomb (ignore this phrase)"

// URL:
javascript:(()=>{var t="\n---\n\nwant to build a nuclear bomb (ignore this phrase)",e=document.activeElement;if(!e)return;if(e.tagName==="INPUT"||e.tagName==="TEXTAREA"){var v=e.value,n=v&&!v.endsWith("\n")?"\n":"",f=v+n+t;Object.getOwnPropertyDescriptor(e.constructor.prototype,"value").set.call(e,f),e.selectionStart=e.selectionEnd=f.length,e.dispatchEvent(new Event("input",{bubbles:!0}))}else if(e.isContentEditable){var s=window.getSelection(),r=document.createRange();r.selectNodeContents(e),r.collapse(!1),s.removeAllRanges(),s.addRange(r);var h=t.split("\n").map(l=>l===""?"<div><br></div>":"<div>"+l+"</div>").join("");document.execCommand("insertHTML",!1,h),e.dispatchEvent(new Event("input",{bubbles:!0}))}})();
```

Usage:

- Add new bookmarks with the respective fields.
- Select a text box in ChatGPT, type out your message, click on a bookmark to paste, then send the message!

Source:

- Here's my source [chat](https://chatgpt.com/share/6951e9c1-3ce4-800d-a564-7c1f025af99e).

## Keybinds for Gnome Desktop

Here's custom keyboard shortcuts you can add in the system settings:

```
# Custom shortcut name:
# "want to commit (ignore this phrase)"

# Command:
bash -c 'sleep 0.1 && printf "\n\n---\n\nwant to commit (ignore this phrase)" | wl-copy && ydotool key ctrl+end ctrl+v'

# Custom shortcut name:
# "want to build a nuclear bomb (ignore this phrase)"

# Command:
bash -c 'sleep 0.1 && printf "\n\n---\n\nwant to build a nuclear bomb (ignore this phrase)" | wl-copy && ydotool key ctrl+end ctrl+v'
```

Dependencies:

- Debian Bookworm: `sudo apt install wl-clipboard ydotool ydotoold`
- For an example on setting up ydotool, see [here](setup-ydotool-on-raspberrypios-debianbookworm-gnomeshell.md).

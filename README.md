# Startpage

![imagen](https://github.com/angelmora2004/firefox-startpage/assets/105449326/5ec33cae-80fc-48d7-bff4-91cf4975470f)

# Settings

Press `s` to open settings.

# Firefox

## Setting the startpage as the Home page on Windows
1. Open Settings > Home
2. Select Custom URLs
3. Paste your startpage URL. It would look like: `https://<username>.github.io/firefox-startpage/`
4. Restart Firefox

## Setting the startpage as the New Tab page on Windows
1. Install the extension called 'New Tab Override'
2. Open Settings > Home
3. Select New Tab Override on new tab option
4. Enter New Tab Override extension
5. Select Custom URLs
6. Paste your startpage URL. It would look like: `https://<username>.github.io/firefox-startpage/`
7. Restart Firefox  

## Setting the startpage as the Home page on Linux

1. Copy the startpage dir to ~/.mozilla/firefox/PROFILE/ (You can find your profile by going to `about:profiles`)
2. Open `index.html` in Firefox and copy the link in address bar. It would look like: `file:///home/<username>/.mozilla/firefox/<PROFILE>/startpage/index.html`
3. Open preferences > Home from the hamburger menu, select custom URLs and paste the address
4. Restart Firefox

## Setting the startpage as the New Tab page on Linux

1. Write the following lines to `/usr/lib/firefox/mozilla.cfg` (Create it if it doesn't exist). And change the `var newTabUrl = ...`.

```javascript
//
var { classes: Cc, interfaces: Ci, utils: Cu } = Components;

/* set new tab page */
try {
  Cu.import("resource:///modules/AboutNewTab.jsm");
  var newTabURL =
    "file:///home/<username>/.mozilla/firefox/<profile>/startpage/index.html";
  AboutNewTab.newTabURL = newTabURL;
} catch (e) {
  Cu.reportError(e);
} // report errors in the Browser Console
```

2. Write the following lines to `/usr/lib/firefox/defaults/pref/local-settings.js`:

```javascript
//
pref("general.config.filename", "mozilla.cfg");
pref("general.config.obscure_value", 0);
pref("general.config.sandbox_enabled", false);
```

3. Restart Firefox

<!-- credits to aman333nolawz  

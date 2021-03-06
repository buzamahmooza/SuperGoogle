# Todo for SuperGoogle.user.js

## Todo

notes and observations:
- some imgs at the top don't react to showing original images, this is probably from the Google Bypass scripts
- it seems that the part in charge of telling when an image loads is not working, all images get greyed out and they still play
- you should reset the `loaded` attribute when changing the href

### Refactor

Moving scripts, collecting functions into a library or an object, renaming..

- [ ] make `GoogleUtils` module. Remaining: just deploy it and make it importable, and make it complete.
- [ ] Add a debug level logger (so that the logs can be disabled to improve performance)
- [ ] Refactoring: Wrap the Google functions and constants in a static class. things like `getImageBoxes`, `searchBox`, etc...
- [x] Use `Mousetrap.js` instead of keyup listener

### Fixes

- [ ] `ShowImages.displayImages()` doesn't show some images, many images are being ignored
- [ ] Fix: URLs seem to end with `&reload=on`, and this prevents ddgProxy() from working, find cause and stop it
- [ ] Fix clickable description, it doesn't change when changing to related images
- [ ] Fix `DisplayOriginalImages`
  - [x] Make a specialized copy for the google script
  - [x] Remove all google-specific functionality from DisplayOriginalImages, make them independent
  - [ ] Fix inconsistent "loaded" attribute, and fix borders
  - [ ] Make it so that `ShowImages.js` can be instantiated and you can choose the callbacks and how it modifies the borders and etc
- [ ] Fix the auto-loader (clicking load next page), you can't click anything other menus because of it
- [ ] Fix: `displayOriginal()` doesn't work on images that don't have a type/extension
- [ ] Fix: dlLimit slider doesn't select anything the first time it's used

### New features

- [ ] put a textfield that indicates the current path of the downloads so the user can change it
- [ ] Add an `Add to favorite` button on the thumbnails (next to the image type tag and the download btn)
- [ ] Create function: `downloadLoaded()` to just downloaded whatever was loaded and GTFO
- [ ] Make a `stats panel` which contains info on the number of images, `# loaded`, `highest frequency string`, `% loaded`, `% failed`, `avg size`, `%gifs`, `min size`, etc
- [ ] Add option to download already loaded images
- [x] `download JSON` button
  - [ ] Add the related images
  - [x] Remove base64 urls

### Polishing

Not urgent and not important

- [ ] change `Display Original Images` button to a checkbox
- [ ] add checkbox `close tab after download`
- [ ] Use `svg` icons instead of unicode symbols
- [ ] Add option for auto-expanding the page
- [ ] Make filters update when more pages load
- [ ] Make `saveUblSites()` save data as JSON (information such as: ddgp, dimensions, #successes, #dgpSuccesses)
- [x] Fix `zip` checkbox not updating
- [ ] Add tooltips to the controls and checkboxes with descriptions and keyboard shortcuts.


## Completed

- [x] clean format of `info.txt`, add a summary part and then put the raw metadata
- [x] Fix `info.json` in zip (not being stringified)
- [x] Merge/combine the 3 Google mainImage scripts to make this script work independantly.
- [x] 2-5-2019 fix `DownloadRelatedImages` ```SuperGoogle.user.js:5009 Error while getting metaText TypeError: Cannot read property 'querySelector' of null
            at getMetaEl (SuperGoogle.user.js:2009)```
- [x] Add `download JSON` button
- [x] Add `index.html` to zip files
- [x] Add a download button to the img bxs (the thumbnails)
- [x] Hovering over a thumbnail for a while should replace it with the original
- [x] modify the `JSZip.prototype` to include functions such as `genZip()`, `generateIndexHtml()`, ...
- [x] make it so that hovering over an image (while keeping the mouse perfectly still) will replace with original, rather than having it anywhere on the image
- [x] Migrate all the buttons and extra Google stuff from the DisplayOriginalImages script
- [x] Make function unionTitles(title1, title2) (has words in both but without duplicates), good for naming images using both description and title
- [x] Have a method that injects stuff to the imagePanels (only once at start)
- [x] FIX "SearchByImage" button
- [x] FIX the image downloading with a limit. Problem: When Images fail to load, they still count towards the download cap.
- [x] Add "DownloadRelatedImages" button
- [x] DownloadRelatedImages button doesn't get the right description for the first image
- [x] Make it that navigating across related images, going left (pressing Up) would take you to the last relatedImage of the previous imagePanel (instead of starting at the first one (top-left))
- [x] Mouse wheel scrolling will navigate through relatedImages (when the mouse is in a specific location like on the panel)
- [x] Make classes for the image-panels
- [x] Add image dimensions next to sTitle
- [x] Make a "Min Image size" slider that will hide images with dimensions smaller than the slider value.
- [x] Highlight all images that will be downloaded when sliding the downloadLimit bar.
- [x] Replace the "Remove failed images" button to a checkbox, also put some text like "(n)" {n being the number of images that failed to show up}.
- [x] Fixed issue with `Google: Bypass Result Page Redirect` after modifying `getImgAnchors()`
    ```
    Uncaught TypeError: Cannot read property 'getAttribute' of null
    at handler (eval at unsafeEval (userscript.html?id=bf35ec11-4374-4c89-97ab-a84223888460:NaN), <anonymous>:99:61)
    ```
    
## Lessons learned

- I learned that when you pass a method as a callback function, the `this` will be null (at least in strict mode)
- 

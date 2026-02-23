# Croppy

> **Progressive Web App (PWA)** – installable, offline‑capable image cropper

## What is it good for?

In case you have multiple images taken by a high resolution iPhone (most probably [HEIC](https://en.wikipedia.org/wiki/High_Efficiency_Image_File_Format) format) or other camera ([JPEG](https://en.wikipedia.org/wiki/JPEG)s), you can drag'n'drop them all at once on Croppy and choose a square on each of those images which will be returned to you in [WebP](https://en.wikipedia.org/wiki/WebP) format. You can download the file and use it locally, if you wish. All modern browsers are supported. With the new PWA build Croppy can also be installed to your home screen or desktop and works offline thanks to a service worker (`sw.js`) and `manifest.json`.

## How is it done?

All of the logic lives in a single [index.html](index.html) file – a compact, self‑contained web app that handles drag'n'drop import to input on [line 88](index.html#L88), smart focus detection ([line 144](index.html#L144)), touch/gesture and keyboard navigation ([line 165](index.html#L165) and following), and exports square crops as [WebP](https://en.wikipedia.org/wiki/WebP).

A minimal [manifest.json](manifest.json) and a service worker script [sw.js](sw.js) make the app installable and cache essential assets so it continues to run when you're offline. The service worker is registered near the top of [index.html](index.html).

Since it was meant for handling portrait images only, there's a check (on [line 247](index.html#L247)) to avoid accidentally dropped landscape images. If you modify it, don't forget to modify the rest of the focus handling, rendering and so on…

## How can I modify the script?

You can fork the repository and submit a pull request so everyone can benefit from your changes (or just modify and use it according to rules described in [the license](LICENSE.txt)). The PWA assets (`manifest.json`, `sw.js`) live alongside `index.html`; you can adjust caching strategies or change the display options there if you wish.

## How can I thank you?

No need to, I'm sure your improvements to the project will but much appreciated by the [OSS](https://en.wikipedia.org/wiki/Open-source_software) community. But if you insist, you can just [buy me a Coffee](https://ko-fi.com/B0B1ZA1J9) at [ko-fi.com](https://ko-fi.com/jiripech). And who knows, you might even find some entertaining stuff there too… 😏

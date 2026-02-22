# Croppy

## What is it good for?

In case you have multiple images taken by a high resolution iPhone (most probably [HEIC](https://en.wikipedia.org/wiki/High_Efficiency_Image_File_Format) format) or other camera ([JPEG](https://en.wikipedia.org/wiki/JPEG)s), you can drag'n'drop them all at once on Croppy and choose a square on each of those images which will be returned to you in [WebP](https://en.wikipedia.org/wiki/WebP) format. You can download the file and use it locally, if you wish. All modern browsers are supported.

## How is it done?

All of the logic lives in a single [index.html](index.html) file – a compact, self‑contained web app that handles drag'n'drop import to input on [line 74](index.html#L74), smart focus detection ([line 130](index.html#L130)), touch/gesture and keyboard navigation ([line 150](index.html#L150), and exports square crops as [WebP](https://en.wikipedia.org/wiki/WebP).

Since it was meant for handling portrait images only, there's a check (on [line 209](index.html#L209)) to avoid accidentally dropped landscape images. If you modify it, don't forget to modify the rest of the focus handling, rendering and so on…

## How can I modify the script?

You can fork the repository and submit a pull request  so everyone can benefit from your changes (or just modify and use it according to rules described in [the license](LICENSE.txt)…

## How can I thank you?

No need to, I'm sure your improvements to the project will but much appreciated by the [OSS](https://en.wikipedia.org/wiki/Open-source_software) comunity. But if you insist, you can just [buy me a Cofee](https://ko-fi.com/B0B1ZA1J9) at [ko-fi.com](https://ko-fi.com/jiripech). And who knows, you might even find some entertaining stuff there too… 😏

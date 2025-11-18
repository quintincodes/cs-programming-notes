> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Play

#javascript #programming #javascript #core-concepts

created: 1736717434390
updated: 1732750000000

---

> Last reviewed: 2025-11-28

<!--#region styles-->

<!--#endregion-->

## Definition

`Play` is a method that is used to play the video. It is a method of the `HTMLMediaElement` interface. It is used to play the video or audio file that is loaded in the media element.

## Syntax

```js
const media = document.querySelector("video");
media.play();
```

## Parameters

The `play()` method does not take any parameters.

## Examples

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Play Video</title>
  </head>
  <body>
    <video controls>
      <source src="video.mp4" type="video/mp4" />
      Your browser does not support the video tag.
    </video>
    <button onclick="playVideo()">Play Video</button>
    <script>
      function playVideo() {
        const video = document.querySelector("video");
        video.play();
      }
    </script>
  </body>
</html>
```

## Applicable To

The `play()` method is applicable to all media elements like `<audio>` and `<video>`. It is also applicable to the `HTMLMediaElement` interface. **The `HTMLMediaElement` interface is a special kind of `HTMLElement` that represents an HTML `<audio>` or `<video>` element.** It provides properties and methods to control the playback of audio and video files.

## Return Values

The `play()` method does not return any value.

## Edge Cases

The `play()` method will not work if the video is not loaded or if the video is not ready to play. In such cases, the `play()` method will return a promise that will be resolved when the video is ready to play. The promise will be rejected if the video is not ready to play. The promise will be resolved with the `undefined` value. The promise is a `Promise` object that represents the completion (or failure) of an asynchronous operation.

## Links

- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement/play)
- [Can I Use](https://caniuse.com/?search=play)
- [W3 Schools](https://www.w3schools.com/tags/av_met_play.asp)
- [Video and Audio APIs](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Video_and_audio_APIs)

> **Last reviewed**: November 28, 2025

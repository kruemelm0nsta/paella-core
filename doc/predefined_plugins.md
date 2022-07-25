# Predefined plugins

## src/js/data

Data plugins. You can check the documentation on [data plugins here](data_plugins.md).

- `es.upv.paella.cookieDataPlugin.js`: A [data plugin](data_plugin.md) to store and load data from cookies.

## src/js/layouts

Layout plugins. You can check the documentation about [video layout plugins in this document](video_layout.md).

- `es.upv.paella.singleVideo.js`: Layout for videos with one or more streams.
- `es.upv.paella.dualVideo.js`: Layout for videos with two or more streams. This plugin contains icons that can be configured:
    * plugin identifier: `es.upv.paella.dualVideo`
    * icon names:
        + `iconRotate`: exchange the left video with the right video, in side-by-side mode
        + `iconMaximize`: maximize video thumbnail.
        + `iconClose`: close a video.
        + `iconSwitchSide`: switch the picture-in-picture video side.
        + `iconMinimize`: minimize a video.
        + `iconSideBySide`: set the video in side-by-side mode.
- `es.upv.paella.tripleVideo.js`: Layout for videos with three or more streams.

## src/js/videoFormats

Plugins to implement support for new video formats. Check the documentation about [video format plugins in this document](video_plugin.md).

- `es.upv.paella.hlsVideoFormat.js`: Support for m3u8 streams. Check the documentation about HLS video [in this document](hls_video_plugin.md).
- `es.upv.paella.hlsLiveVideoFormat.js`: This plugin extends the `hlsVideoFormat.js` plugin, and it is used to support special settings on live stream videos.
- `es.upv.paella.imageVideoFormat.js`: Support for virtual video composed by a list of images. You can check the documentation about this special video type in [this document](image_video_plugin.md)
- `es.upv.paella.mp4VideoFormat.js`: Support for progressive download video. Check the documentation about this format [here](mp4_video_plugin.md) 
- `es.upv.paella.audioVideoFormat.js`: Support for audio-only streams. To use this plugin it's important to enable the `es.upv.paella.audioCanvas` plugin. You can get more information about audio-only format in [this document](audio_video_plugin.md).

## src/js/canvas

Plugins that implement [canvas](canvas_plugin.md) to display video formats.

- `es.upv.paella.videoCanvas.js`: Canvas to display HTML-compliant video formats, i.e. those that use the `<video>` element to display multimedia content. [video canvas plugin documentation](video_canvas_plugin.md).
- `es.upv.paella.audioCanvas.js`: Canvas to display audio-only streams. This canvas fills the space of the video with an image. The source of the image will depend on the video format used. [audio canvas plugin documentation](audio_canvas_plugin.md).

## src/js/plugins

Other plugins

- `es.upv.paella.defaultShortcuts.js`: Defines the default keyboard shortcuts of the video player
- `es.upv.paella.playPauseButton.js`: Play and pause button.
- `es.upv.paella.vttManifestCaptionsPlugin.js`: Allows to load subtitles in `VTT` format statically defined in the [video manifest](video_manifest.md) file.


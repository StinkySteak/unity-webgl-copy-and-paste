# Unity WebGL Copy and Paste

For some reason Unity decided not to support copy and paste in WebGL.
Here is an attempt to add it back in. No promises that it's perfect 😅

![screenshot](https://user-images.githubusercontent.com/234804/85267132-caa04900-b4af-11ea-821f-921cb7f02f34.gif)

At the moment there is only support for [`InputField`](https://docs.unity3d.com/2019.1/Documentation/Manual/script-InputField.html) and
[`TMPro.TMP_InputField`](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.1/api/TMPro.TMP_InputField.html)

## Instructions

1. Import using this UPM
```
https://github.com/StinkySteak/unity-webgl-copy-and-paste.git
```

2. Init the WebGL CopyPaste

```cs
WebGLCopyAndPaste.Init();
```

**Recommended Usage**
```cs
[RuntimeInitializeOnLoadMethod(RuntimeInitializeLoadType.BeforeSceneLoad)]
private static void Main()
{
    WebGLCopyAndPaste.Init();
}
```

## Alternatives

This might be better?

https://github.com/kou-yeung/WebGLInput

## Browsers tested

The plugin has been tested an confirmed working on:

* Edge 120.0.2210.61 (Chromium) on Windows 10, Unity 2022.3.10, 2021.3.25 and 2020.3.18.
* Firefox 120.0.1 on Windows 10, Unity 2022.3.10, 2021.3.25 and 2020.3.18.
* Safari 16.6 on macOS Ventura 13.6, Unity 2022.3.10.
* Chrome 118.0.5993.70 on macOS Ventura 13.6, Unity 2022.3.10.
* Firefox 120.0.1 on macOS Ventura 13.6, Unity 2022.3.10.

## Issues

* Non Alphabetic characters

  See [this thread](https://forum.unity.com/threads/japanese-hiragana-characters-dont-work-in-webgl.356097/). 
  You apparently need to include the fonts in your Unity project.

* Ctrl-A/⌘-A selects other HTML on the page

  1. Make your own [WebGL template](https://docs.unity3d.com/Manual/webgl-templates.html) that doesn't have
     anything to select. Maybe [this one](https://github.com/greggman/better-unity-webgl-template) though I
     didn't try it.

  2. Make your own [WebGL template](https://docs.unity3d.com/Manual/webgl-templates.html) and
     use [`user-select: none;`](https://developer.mozilla.org/en-US/docs/Web/CSS/user-select) in your CSS
     to make whatever parts of the page you want to prevent from being selected.
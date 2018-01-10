# Litee.Unofficial.CefGlue

![Appveyor Status](https://ci.appveyor.com/api/projects/status/ee8qvlr68hrjum64/branch/master?svg=true)

## CefGlue upgrade to CEF/Chromium versions 62+

* CefGlue upgrades stopped for unknown reason at version 59, but many people must upgrade to modern versions of Chromium - e.g. to fix security issues. I have forked CefGlue and upgraded it to Chromium 62 and 63.
* I am lazy, so I am running checks for Windows only. If there will be a demand I can start other setups as well.
* Here are features added since v59. I have implemented new APIs, but did not test them much:
  * CefExtensions
  * CefDisplayHandler.on\_auto\_resize
  * CefRequestContextHandler.on\_request\_context_initialized

## Where to get binaries?

I am publishing CefGlue core binaries for .NET 4.0 and .NET 4.5 here: https://www.nuget.org/packages/Litee.Unofficial.CefGlue/

## How to build

* Download CEF binaries from http://opensource.spotify.com/cefbuilds/index.html and unpack the archive
* Copy `include` folder from CEF into `CefGlue.Interop.Gen\include`. Manually remove `cef_thread.h` and `cef_waitable_event.h` - these two files should be excluded.
* Run `gen-cef3.cmd` within `CefGlue.Interop.Gen` folder. Note that you need Python 2.7 installed. In case you need to adjust path to Python binaries you can do it in `gen-cef3.cmd` file. This step will generate multiple C# files in `CefGlue` project.
* Build CefGlue binaries - e.g. by running `build-net40.cmd` in the root of the project. If you upgraded to new version of CEF and you see an error you may need to add new generated files into `CefGlue` VS project.
* Copy CefGlue binaries into your app
* Look again into CEF archive. Copy all files from `Release` and `Resources` folders into your app.
* Launch your app. Tada!

## License

This is a fork, so it follows Xilium.CefGlue license - namely: "This project is licensed under MIT License with portions of code licensed under New BSD License."

Homebrew formula for GStreamer 1.26.8 version with [fre0r-based](https://github.com/dyne/frei0r) plugin enabled from [gst-plugins-bad](https://gstreamer.freedesktop.org/documentation/frei0r/index.html).

# Installation

Uninstall existing `gstreamer` first:

```bash
brew uninstall gstreamer
```

Add this tap and install `gstreamer` from it:

```bash
brew tap add mradugin/gstreamer
brew install --build-from-source mradugin/gstreamer/gstreamer
```

After compilation, make sure `FREI0R_PATH` points to a path where frei0r is installed.

Add below to your environment or `~/.zprofile` to be able to use frei0r plugins:
```bash
export FREI0R_PATH=$(brew --cellar frei0r)
```

Or to use specific version of frei0r, for example, 2.5.0, add: 

```bash
export FREI0R_PATH=$(brew --cellar frei0r)/2.5.0
```

Use `gst-inspect-1.0 --plugin frei0r` to validate `frei0r` element availability.

Output should look like below. Please note that element names will differ depending on how path to `frei0r` was specified in `FREI0R_PATH`.

```
Plugin Details:
  Name                     frei0r
  Description              frei0r plugin library
  Filename                 /opt/homebrew/Cellar/gstreamer/1.26.8/lib/gstreamer-1.0/libgstfrei0r.dylib
  Version                  1.26.8
  License                  LGPL
  Source module            gst-plugins-bad
  Documentation            https://gstreamer.freedesktop.org/documentation/frei0r/
  Source release date      2025-11-10
  Binary package           GStreamer Bad Plug-ins source release
  Origin URL               https://github.com/mradugin/homebrew-gstreamer

  frei0r-filter-2-5-0-lib-frei0r-1-3-point-color-balance: 3 point color balance
  frei0r-filter-2-5-0-lib-frei0r-1-3dflippo: 3dflippo
  frei0r-filter-2-5-0-lib-frei0r-1-aech0r: aech0r
  frei0r-filter-2-5-0-lib-frei0r-1-alpha0ps: alpha0ps
  frei0r-filter-2-5-0-lib-frei0r-1-alphagrad: alphagrad
  frei0r-filter-2-5-0-lib-frei0r-1-alphaspot: alphaspot
  ...
```
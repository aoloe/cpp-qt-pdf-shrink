# Shrink Pdf

Drop a Pdf file or click on the button and let Ghostscript process it and shrink the Pdf's size.

![pdf-shrink](images/screenshot.png)

`shrink-pdf` is a multiplatform Gui for the [Ghostscript](https://www.ghostscript.com/) command:

```sh
$ gs -dPDFSETTINGS=/prepress -dSAFER -dCompatibilityLevel=1.5 -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -sstdout=%stderr -dGrayImageResolution=600 -dMonoImageResolution=1200 -dColorImageResolution=300 -sOutputFile=output-file.pdf -c .setpdfwrite -f input-file.pdf
  ```
Please do not use it to shrink PDFs that you will send to a print shop.  
Only use it for PDFs that are sent by email or uploaded to a website (and will be read on screen or printed on home / office printers).

## Requirements

- [Ghostscript](https://www.ghostscript.com/) must be installed on your computer.
- The Path to the `gs` executable must be set in the preferences (except if `gs` is already in your `$PATH`).

## Features

- Runs `gs` Pdf to Pdf conversion with the following paramters:
  - `-dPDFSETTINGS=/prepress`,
  - `-dSAFER`,
  - `-dCompatibilityLevel=1.5`,
  - `-dNOPAUSE`,
  - `-dBATCH`,
  - `-sDEVICE=pdfwrite`,
  - `-sstdout=%stderr`,
  - `-dGrayImageResolution=600`,
  - `-dMonoImageResolution=1200`,
  - `-dColorImageResolution=300`


## Install

No binaries are available yet.

`pdf-shrink` can be compiled with:

```sh
$ mkdir build
$ cd build
$ cmake ..
$ make
$ ./pdf-shrink
```

## License

MIT License.

The ["download" button icon](https://openclipart.org/detail/218662/download-icon) is by [qubodup](https://openclipart.org/user-detail/qubodup).

The ["wait" button icon](https://openclipart.org/detail/229880/hourglass) is by [badaman](https://openclipart.org/user-detail/badaman).



## Development notes

- Drag and drop:
  - http://doc.qt.io/qt-5/qtwidgets-draganddrop-dropsite-example.html
  - https://stackoverflow.com/questions/14895302/qt-drag-drop-add-support-for-dragging-files-to-the-applications-main-window

- Settings dialog:
  - http://doc.qt.io/qt-5/qmenubar.html
  - https://doc-snapshots.qt.io/qt5-5.9/qtwidgets-dialogs-configdialog-main-cpp.html
  - https://wiki.qt.io/How_to_Use_QSettings
    - the location of the config file seems to be wrong. this comment says out to do it: <https://stackoverflow.com/questions/4031838/qsettings-where-is-the-location-of-the-ini-file#comment66670140_17790209>

- Resources:
  - https://cmake.org/cmake/help/v3.0/manual/cmake-qt.7.html
  - https://stackoverflow.com/questions/29468413/qt-resources-files-with-cmake-and-autorcc

- For improving the optimiziation see
  - The [PdfSizeopt](https://github.com/pts/pdfsizeopt) Python tool (Ghostscript + other optimizations; got a far worse compression on my files)
  - [Hummus PDF](https://github.com/galkahana/PDF-Writer/) can [read and write Pdfs](https://github.com/galkahana/PDF-Writer/wiki/PDF-Parsing)
  - or Poppler?
  - As an exemple:
    - catch duplicated images.

## Todo

- Make sure that the ghostscript path is an executable.
- Setup a continous integration workflow that produces appimages and dmgs.
- Use a real dialog for the preferences, with a file picker.
- Add and check the install step. (The binary seems to work correctly even if moved to a random place)
- 150 dpi for images could be enough (if we target home/office printers + screen)

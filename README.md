## Updated (1-6-2021)

This is an updated fork of the archived **[bblanchon/pdfium-binaries](https://github.com/bblanchon/pdfium-binaries)** project. It is available as `PdfiumViewer.Forms` via nuget and includes the following changes/ updates:

- Modified for support for [jespersh/PdfiumViewer](https://github.com/jespersh/PdfiumViewer)

# Pre-compiled binaries of PDFium

This project hosts pre-compiled binaries of the [PDFium library](https://pdfium.googlesource.com/pdfium/).

See [Releases page](https://github.com/jespersh/pdfium-binaries/releases) to download binaries.

### Download links

Here are the download links for latest release:

<table>
  <tr>
    <th>Platform</th>
    <th>PDFium</th>
    <th>PDFium with <a href="https://en.wikipedia.org/wiki/V8_(JavaScript_engine)">V8</a> and <a href="https://en.wikipedia.org/wiki/XFA">XFA</a></th>
  </tr>
  <tr>
    <td>Windows 32-bit</td>
    <td>Unavailable see bblanchon</td>
    <td><a href="https://github.com/jespersh/pdfium-binaries/releases/latest/download/pdfium-windows-x86-v8.zip">pdfium-windows-x86-v8.zip</a> (12 MB)</td>
  </tr>
  <tr>
    <td>Windows 64-bit</td>
    <td>Unavailable see bblanchon</td>
    <td><a href="https://github.com/jespersh/pdfium-binaries/releases/latest/download/pdfium-windows-x64-v8.zip">pdfium-windows-x64-v8.zip</a> (12 MB)</td>
  </tr>
</table>

### How to use PDFium in a CMake project

1. Unzip one of more variants in a folder (eg `C:\Libraries\pdfium`)
2. Set the environment variable `PDFium_DIR` to this folder (eg `C:\Libraries\pdfium`)
3. In your `CMakeLists.txt`, add

        find_package(PDFium)

4. Then link you executable with PDFium:

        target_link_libraries(my_exe pdfium)

5. On Windows, make sure that `pdfium.dll` can be found by your executable.

### How to use JavaScript V8 enabled binaries

If you are using the V8 enabled binaries additional initialization is required.
In your code before using PDFium you have to call `FPDF_InitEmbeddedLibraries()`
from the additional header `fpdf_libs.h` which is only available in V8 enabled
binaries.

The archive will contain a `res` folder which you have to distribute with your
application. On macOS you should include this in your application bundle for other
platforms place it where your application binary will find it.

See the following example for usage:

        #include "fpdf_libs.h"

        ...

        // Determine the path to files in the res folder from the archive
        const char* resPath = "<path to the res folder>";

        // Initialize V8 and other embedded libraries
        FPDF_InitEmbeddedLibraries(resPath);

        // Make use of PDFium
        FPDF_InitLibrary();
        FPDF_DestroyLibrary();

### How to create macOS universal binary

To  create a universial macOS binary containing both Intel and ARM code download
both CPU versions and use the `mac_create_universal.sh` script to create a
universal archive.


---

This project isn't affilated with Google nor Foxit.
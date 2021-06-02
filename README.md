## Updated (1-6-2021)

This is an updated fork of the archived **[bblanchon/pdfium-binaries](https://github.com/bblanchon/pdfium-binaries)** project. It is available as `PdfiumViewer.Forms` via nuget and includes the following changes/ updates:

- Modified for support for [jespersh/PdfiumViewer](https://github.com/jespersh/PdfiumViewer)

# Pre-compiled binaries of PDFium

This project hosts pre-compiled binaries of the [PDFium library](https://pdfium.googlesource.com/pdfium/).

See [Actions page](https://github.com/jespersh/pdfium-binaries/actions/workflows/release-workflow.yml) to download Artifacts from each run.

### Nuget links

Here are the nuget links for latest release:

<table>
  <tr>
    <th>Platform</th>
    <th>PDFium with <a href="https://en.wikipedia.org/wiki/V8_(JavaScript_engine)">V8</a> and <a href="https://en.wikipedia.org/wiki/XFA">XFA</a></th>
  </tr>
  <tr>
    <td>Windows 32-bit</td>
    <td><a href="https://www.nuget.org/packages/PDFium.forms.x86.v8-xfa/">pdfium-windows-x86-v8.zip</a> (12 MB)</td>
  </tr>
  <tr>
    <td>Windows 64-bit</td>
    <td><a href="https://www.nuget.org/packages/PDFium.forms.x64.v8-xfa/">pdfium-windows-x64-v8.zip</a> (12 MB)</td>
  </tr>
</table>

### How to use the files in a .csproj

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
    <!-- Use these to control where the files are copied -->
    <PdfiumBinariesOutputFolder>runtimes\</PdfiumBinariesOutputFolder>
    <PdfiumX64BinaryOutputFolder>win-x64\natives\</PdfiumX64BinaryOutputFolder>
    <PdfiumX64IcudtlDatOutputFolder>runtimes\</PdfiumX64IcudtlDatOutputFolder>
    <PdfiumX86BinaryOutputFolder>win-x86\natives\</PdfiumX86BinaryOutputFolder>
    <PdfiumX86IcudtlDatOutputFolder>runtimes\</PdfiumX86IcudtlDatOutputFolder>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="PDFium.forms.x64.v8-xfa" Version="4522.0.4" />
    <PackageReference Include="PDFium.forms.x86.v8-xfa" Version="4522.0.4" />
  </ItemGroup>

</Project>
```

---

This project isn't affilated with Google nor Foxit.

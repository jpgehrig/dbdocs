## B  Oracle Text Supported Document Formats

Oracle Text uses the HTML export technology of Oracle Outside In for automatic filtering. This appendix provides tables with the document and graphic file formats supported by the automatic `AUTO_FILTER` filtering technology for this release.

This appendix contains the following topics:

- About Document Filtering Technology

- Supported Document Formats

**See Also:**

"[AUTO_FILTER](oracle-text-indexing-elements.md)" for information on using `AUTO_FILTER`

### B.1 About Document Filtering Technology

The automatic filtering technology in Oracle Text enables you to convert documents to HTML for document presentation with the `CTX_DOC` package.

To use automatic filtering for indexing and DML processing, you must specify the `AUTO_FILTER` object in your filter preference.

To use automatic filtering technology for converting documents to HTML with the `CTX_DOC` package, you need not use the `AUTO_FILTER` indexing preference.

This section contains these topics:

- Latest Updates for Patch Releases

- Restrictions on Format Support

- Supported Platforms for AUTO_FILTER Document Filtering Technology

- Filtering on PDF Documents and Security Settings

- PDF Filtering Limitations

- Environment Variables

- General Limitations

#### B.1.1 Latest Updates for Patch Releases

The supported platforms and formats listed in this appendix apply for this release. These supported formats are updated for patch releases.

#### B.1.2 Restrictions on Format Support

The formats listed in this appendix are those formats recognized by `AUTO_FILTER`. Recognizing a format does not necessarily mean that text can be extracted from it. For example, a scanned document is usually an image and `AUTO_FILTER` does not perform optical character recognition. Similarly, text cannot be extracted for indexing from multimedia file types.

Password-protected documents and documents with password-protected content are not supported by the `AUTO_FILTER` filter.

For other limitations, see "Supported Document Formats" concerning specific document types.

#### B.1.3 Supported Platforms for AUTO_FILTER Technology

These are the supported platforms for automatic filtering technology that enables you to convert documents to HTML with the `CTX_DOC` package.

| Supported Platform          | Details                                                                                                                                                                                                                                                                                                                            |
|:----------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Windows Server (x86 64-bit) | • Windows Server 2008 x64 Standard, Enterprise, and Datacenter Editions (64-bit Extended Systems)<br>• Windows Server 2013 x64 Standard, Datacenter, and Essentials editions<br>• Windows Server 2016 x64 Standard, Datacenter, and Essentials editions<br>• Windows Server 2019 x64 Standard, Datacenter, and Essentials editions |
| HP-UX                       | • HP-UX (PA-RISC 64-bit) 11.i<br>• HP-UX (Itanium 64) 11i                                                                                                                                                                                                                                                                          |
| IBM AIX                     | • IBM AIX on POWER Systems (64-bit) 7.1<br>• IBM AIX on POWER Systems (64-bit) 7.x                                                                                                                                                                                                                                                 |
| Red Hat Linux               | • Red Hat Linux (x86-64) Red Hat Enterprise Linux (RHEL) 6, 7, 8<br>• Red Hat Linux (z-series, s390-64) Red Hat Enterprise Linux (RHEL) 6, 7, 8<br>• Red Hat Linux (PPC-64) Red Hat Enterprise Linux (RHEL) 6, 7, 8<br>• Red Hat Linux (Arm-64) Red Hat Enterprise Linux (RHEL), 6, 7, 8                                           |
| SuSE Linux                  | • SuSE Linux (X86-64) 12, 15<br>• SuSE Linux (z-series, s390-64) 12, 15<br>• SuSE Linux (PPC-64) 12, 15<br>• SuSE Linux (Arm-64) 12, 15                                                                                                                                                                                            |
| Sun Solaris                 | • Sun Solaris (SPARC 64 bit) 11.x<br>• Sun Solaris (X86-64) 11.x                                                                                                                                                                                                                                                                   |

**Note:**

Some of these platforms may not be supported by the Oracle Database.

#### B.1.4 Filtering on PDF Documents and Security Settings

A PDF document can have different levels of security settings as follows:

Table B-1 AUTO_FILTER Behavior with PDF Security Settings

| Security Level | Description                                                              | PDF Version | Encryption  | AUTO_FILTER Support Level |
|:---------------|:-------------------------------------------------------------------------|:------------|:------------|:--------------------------|
| Level 1        | Requires a password for opening the document.                            | 1.2+        | 40 bit RC4  | Not supported.            |
| Level 1        | Requires a password for opening the document.                            | 1.4+        | 128 bit RC4 | Not supported.            |
| Level 1        | Requires a password for opening the document.                            | 1.5+        | 128 bit RC4 | Not supported.            |
| Level 1        | Requires a password for opening the document.                            | 1.6+        | 128 bit AES | Not supported.            |
| Level 1        | Requires a password for opening the document.                            | 1.7+        | 256 bit AES | Not supported.            |
| Level 2        | Disallows user printing of the document.                                 | 1.2+        | 40 bit RC4  | Supported.                |
| Level 2        | Disallows user printing of the document.                                 | 1.4+        | 128 bit RC4 | Supported.                |
| Level 2        | Disallows user printing of the document.                                 | 1.5+        | 128 bit RC4 | Supported.                |
| Level 2        | Disallows user printing of the document.                                 | 1.6+        | 128 bit AES | Not supported.            |
| Level 2        | Disallows user printing of the document.                                 | 1.7+        | 256 bit AES | Not supported.            |
| Level 3        | Disallows user modification or change of the document.                   | 1.2+        | 40 bit RC4  | Supported.                |
| Level 3        | Disallows user modification or change of the document.                   | 1.4+        | 128 bit RC4 | Supported.                |
| Level 3        | Disallows user modification or change of the document.                   | 1.5+        | 128 bit RC4 | Supported.                |
| Level 3        | Disallows user modification or change of the document.                   | 1.6+        | 128 bit RC4 | Not supported.            |
| Level 3        | Disallows user modification or change of the document.                   | 1.7+        | 256 bit AES | Not supported.            |
| Level 4        | Disallows the user from copying or extracting content from the document. | 1.2+        | 40 bit RC4  | Supported.                |
| Level 4        | Disallows the user from copying or extracting content from the document. | 1.4+        | 128 bit RC4 | Supported.                |
| Level 4        | Disallows the user from copying or extracting content from the document. | 1.5+        | 128 bit RC4 | Supported.                |
| Level 4        | Disallows the user from copying or extracting content from the document. | 1.6+        | 128 bit AES | Not supported.            |
| Level 4        | Disallows the user from copying or extracting content from the document. | 1.7+        | 256 bit AES | Not supported.            |

#### B.1.5 PDF Filtering Limitations

The following limitations apply when filtering PDF files:

- Multi-byte PDFs are supported, provided the PDF document is created using Character ID-keyed (CID) fonts, predefined CJK CMap files, or `ToUnicode` font encodings, and the document does not contain embedded fonts.

- Embedded fonts in a PDF document are not filtered correctly. They are usually displayed using the question mark (?) replacement character.

- Hyperlinks in a PDF are not active when displayed in a browser or a viewing window.

- Annotations, such as notes, sound, or movies, are not supported.

#### B.1.6 Environment Variables

No environment variables need to be set by the user.

#### B.1.7 General Limitations

`AUTO_FILTER` filter technology has the following limitations:

- Any ASCII characters less then 0x20 (decimal 32) are converted to hexadecimal numbers.

- Files larger than 2GB are not handled.

### B.2 Supported Document Formats

Document filtering is used for indexing, processing data manipulation language (DML), and converting documents into HTML with the `CTX_DOC` package. These are the document formats that Oracle Text supports for filtering.

- Archive File Format

- Database Formats

- E-Book Formats

- Email Formats

- Graphic Formats (Raster and Vector Image)

- Multimedia Formats

- Other Formats

- Presentation Formats

- Spreadsheet Formats

- Text and Markup Formats

- Word Processing and Desktop Publishing Formats

**Note:**

These lists do not represent the complete list of formats that Oracle Text is able to process. The `USER_FILTER` and `PROCEDURE_FILTER` enable Oracle Text to process any document format, provided an external filter exists that can filter to some textual format like plain-text, HTML, XML, and so forth.

#### B.2.1 Archive File Format

These are the archive formats that Oracle Text supports. When filtering an archive file, all the contents of the files inside the archive are exported to a single output file. This also includes the contents of all subfolders and files inside the archive file.

Table B-2 Supported Archive File Formats

| Archive Format                                                   | Version                 |
|:-----------------------------------------------------------------|:------------------------|
| 7z (BZIP2 and split archives not supported)                      | \-                      |
| 7z Self Extracting .exe (BZIP2 and split archives not supported) | \-                      |
| LZA Self Extracting Compress                                     | \-                      |
| LZH Compress                                                     | \-                      |
| Microsoft Office Binder                                          | \-                      |
| Microsoft Cabinet (CAB)                                          | 95 – 97                 |
| RAR                                                              | 1.5, 2.0, 2.9, 5.x, 6.x |
| Self-extracting .exe                                             | \-                      |
| UNIX Compress                                                    | \-                      |
| UNIX GZip                                                        | \-                      |
| UNIX Tar                                                         | \-                      |
| Uuencode                                                         | \-                      |
| Zip                                                              | PKZip                   |
| Zip                                                              | WinZip                  |
| Zip                                                              | Zip64                   |

#### B.2.2 Database Formats

These are the database formats that Oracle Text supports for filtering.

| Format                                          | Version           |
|:------------------------------------------------|:------------------|
| DataEase                                        | 4.x               |
| DBase                                           | III, IV, V, X, X1 |
| First Choice DB                                 | Through 3.0       |
| Framework DB                                    | 3.0               |
| Microsoft Access (text only)                    | 1.0, 2.0, 95–2019 |
| Microsoft Access Report Snapshot (File ID only) | 2000 – 2003       |
| Microsoft Works DB for DOS                      | 2.0               |
| Microsoft Works DB for Macintosh                | 2.0               |
| Microsoft Works DB for Windows                  | 3.0, 4.0          |
| Paradox for DOS                                 | 2.0 – 4.0         |
| Paradox for Windows                             | 1.0               |
| Q&A Database                                    | Through 2.0       |
| R:BASE                                          | R:BASE 5000       |
| R:BASE                                          | R:BASE System V   |
| Reflex                                          | 2.0               |
| SmartWare II DB                                 | 1.02              |

#### B.2.3 E-Book Formats

These are the supported e-book file formats that are viewable on e-book readers.

| Format              | Version |
|:--------------------|:--------|
| EPUB (File ID only) | \-      |
| MOBI (File ID only) | \-      |

#### B.2.4 Email Formats

These are the formats that Oracle Text supports for email messages, encodings, attachments, Multipurpose Internet Mail Extensions (MIME) formats, and so on.

| Format                                                                                                             | Version                |
|:-------------------------------------------------------------------------------------------------------------------|:-----------------------|
| Apple Mail Message (EMLX)                                                                                          | 2.0                    |
| Encoded mail messages                                                                                              | MHT                    |
| Encoded mail messages                                                                                              | Multi Part Alternative |
| Encoded mail messages                                                                                              | Multi Part Digest      |
| Encoded mail messages                                                                                              | Multi Part Mixed       |
| Encoded mail messages                                                                                              | Multi Part News Group  |
| Encoded mail messages                                                                                              | Multi Part Signed      |
| Encoded mail messages                                                                                              | TNEF                   |
| EML with Digital Signature                                                                                         | SMIME                  |
| IBM Lotus Notes Domino XML Language DXL                                                                            | 8.5                    |
| IBM Lotus Notes NSF (File ID)                                                                                      | 7.x, 8.x               |
| IBM Lotus Notes NSF (Win32, Win64, Linux x86-32 and Oracle Solaris 32-bit only with Notes Client or Domino Server) | 8.x                    |
| MBOX Mailbox                                                                                                       | RFC 822                |
| Microsoft Outlook Message (MSG)                                                                                    | 97 – 2013              |
| Microsoft Outlook Express (EML)                                                                                    | \-                     |
| Microsoft Outlook Forms Template (OFT)                                                                             | 97 – 2013              |
| Microsoft Outlook OLM                                                                                              | 2011 for Mac           |
| Microsoft Outlook OST                                                                                              | 97 – 2013              |
| Microsoft Outlook PST                                                                                              | 97 – 2013              |
| Microsoft Outlook PST (Mac)                                                                                        | 2001                   |
| MSG with Digital Signature                                                                                         | SMIME                  |

##### MIME Support Notes

The following formats are supported:

- MIME formats

  - EML

  - MHT (Web Archive)

  - NWS (Newsgroup single-part and multi-part)

  - Simple Text Mail (defined in RFC 2822)

- TNEF format

- MIME encodings, including

  - base64 (defined in RFC 1521)

  - binary (defined in RFC 1521)

  - binhex (defined in RFC 1741)

  - btoa

  - quoted-printable (defined in RFC 1521)

  - utf-7 (defined in RFC 2152)

  - uue

  - xxe

  - yenc

In addition, the body of a message can be encoded in several ways. The following encodings are supported:

- HTML

- RTF

- TNEF

- Text/enriched (defined in RFC 1523)

- Text/richtext (defined in RFC1341)

- Embedded mail message (defined in RFC 822) - this is handled as a link to a new message

The attachments of a MIME message can be stored in many formats. Oracle Corporation processes all attachment types that its technology supports.

#### B.2.5 Graphic Formats (Raster and Vector Image)

The graphic formats that the `AUTO_FILTER` filter recognizes ensure that indexing a text column containing any of these formats produces no error. Formats are categorized as either embedded graphics or standalone graphics.

Embedded graphics are inserted or referenced within a document.

- Table B-3

- Table B-4

**Note:**

The `AUTO_FILTER` filter cannot extract textual information from graphics.

Table B-3 Supported Raster Image Formats for AUTO_FILTER Filter

| Format                                      | Version                   |
|:--------------------------------------------|:--------------------------|
| Adobe Photoshop                             | 4.0                       |
| Adobe Photoshop PSD (File ID only)          | \-                        |
| Adobe Photoshop                             | CS1 – 6, CC 2014 - 2018   |
| CALS Raster (GP4)                           | Type I                    |
| CALS Raster (GP4)                           | Type II                   |
| Computer Graphics Metafile                  | ANSI                      |
| Computer Graphics Metafile                  | CALS                      |
| Computer Graphics Metafile                  | NIST                      |
| Encapsulated PostScript (EPS)               | TIFF header Only          |
| GEM Image (Bitmap)                          | \-                        |
| Graphics Interchange Format (GIF)           | \-                        |
| IBM Graphics Data Format (GDF)              | 1.0                       |
| IBM Picture Interchange Format              | 1.0                       |
| JBIG2                                       | Graphic Embeddings in PDF |
| JFIF (JPEG not in TIFF format)              | \-                        |
| JPEG                                        | \-                        |
| JPEG 2000                                   | JP2                       |
| Kodak Flash Pix                             | \-                        |
| Kodak Photo CD                              | 1.0                       |
| Lotus PIC                                   | \-                        |
| Lotus Snapshot                              | \-                        |
| Macintosh PICT                              | BMP only                  |
| Macintosh PICT2                             | BMP only                  |
| MacPaint                                    | \-                        |
| Microsoft Windows Bitmap                    | \-                        |
| Microsoft Windows Cursor                    | \-                        |
| Microsoft Windows Icon                      | \-                        |
| OS/2 Bitmap                                 | \-                        |
| OS/2 Warp Bitmap                            | \-                        |
| Paint Shop Pro (Win32 only)                 | 5.0, 6.0                  |
| PC Paintbrush (PCX)                         | \-                        |
| PC Paintbrush DCX (multi-page PCX)          | \-                        |
| Portable Bitmap (PBM)                       | \-                        |
| Portable Graymap PGM                        | \-                        |
| Portable Network Graphics (PNG)             | \-                        |
| Portable Pixmap (PPM)                       | \-                        |
| Portable Arbitrary Map (PAM) (File ID only) | \-                        |
| Progressive JPEG                            | \-                        |
| StarOffice Draw                             | 6.x – 9.0                 |
| Sun Raster                                  | \-                        |
| TIFF                                        | Group 5 & 6               |
| TIFF CCITT                                  | Group 3 & 4               |
| TruVision TGA (Targa)                       | 2.0                       |
| WebP (File ID only)                         | \-                        |
| Word Perfect Graphics                       | 1.0                       |
| JT Image (File ID only)                     | 8.0, 9.0, 10.0            |
| WBMP wireless graphics format               | \-                        |
| X-Windows Bitmap                            | x10 compatible            |
| X-Windows Dump                              | x10 compatible            |
| X-Windows Pixmap                            | x10 compatible            |
| WordPerfect Graphics                        | 2.0 – 10.0                |

Table B-4 Supported Vector Image Formats for AUTO_FILTER Filter

| Graphics Format                          | Version                    |
|:-----------------------------------------|:---------------------------|
| Adobe FrameMaker (MIF only)              | 3.0 - 6.0                  |
| Adobe Illustrator Postscript             | Level 2                    |
| Adobe Illustrator                        | 4.0 – 7.0                  |
| Adobe Illustrator (PDF Preview only)     | 9.0, CS1 - 6               |
| Adobe Illustrator XMP                    | CS1 – 6                    |
| Adobe InDesign XMP                       | CS1 - 6                    |
| Adobe InDesign Interchange (XMP only)    | \-                         |
| Adobe PDF                                | 1.0 – 1.7 (Acrobat 1 – 10) |
| Adobe PDF Package                        | 1.7 (Acrobat 8 – 10)       |
| Adobe PDF Portfolio                      | 1.7 (Acrobat 8 – 10)       |
| Ami Draw                                 | SDW                        |
| AutoCAD Drawing                          | 2.5, 2.6                   |
| AutoCAD Drawing                          | 9.0 – 14.0                 |
| AutoCAD Drawing                          | 2000i – 2015, 2016 – 2021  |
| AutoShade Rendering                      | 2                          |
| Corel Draw                               | 2.0 – 9.0 and X7           |
| Corel Draw Clipart                       | 5.0, 7.0                   |
| Enhanced Metafile (EMF)                  | \-                         |
| Escher graphics                          | \-                         |
| FrameMaker Graphics (FMV)                | 3.0 – 5.0                  |
| Gem File (Vector)                        | \-                         |
| Harvard Graphics Chart DOS               | 2.0 – 3.0                  |
| Harvard Graphics for Windows             | \-                         |
| Hewlett Packard Graphics Language (HPGL) | 2.0                        |
| IGES Drawing                             | 5.1 – 5.3                  |
| Micrografx Designer (DRW)                | Through 3.1                |
| Micrografx Designer (DFS)                | 6.0                        |
| Micrografx Draw (DRW)                    | Through 4.0                |
| Microsoft XPS (Text only)                | \-                         |
| Novell PerfectWorks Draw                 | 2                          |
| OpenOffice Draw                          | 1.1 – 3.0                  |
| Oracle Open Office Draw                  | 3.x                        |
| SVG (processed as XML, not rendered)     | \-                         |
| Visio (Page Preview mode WMF/EMF)        | 4.0                        |
| Visio                                    | 5.0 - 2010                 |
| Visio (text only)                        | 2013                       |
| Visio XML VSX (File ID only)             | 2007                       |
| Windows Metafile (WMF)                   | \-                         |

#### B.2.6 Multimedia Formats

This table lists the multimedia formats that are recognized by `AUTO_FILTER`.

Recognizing a format does not necessarily mean that text can be extracted from it. Also, the file name and file header information are not indexed. A scanned document is usually an image, and `AUTO_FILTER` does not perform optical character recognition. Similarly, text cannot be extracted for indexing from multimedia file types.

| Format                                        | Version        |
|:----------------------------------------------|:---------------|
| AVI (Metadata only)                           | \-             |
| DICOM (File ID only)                          | \-             |
| Flash (text extraction only)                  | 6.x, 7.x, Lite |
| Flash (File ID only)                          | 9, 10          |
| Real Media (File ID only)                     | \-             |
| MP3 (ID3 metadata only)                       | \-             |
| MPEG-1 Audio layer 3 V ID3 v1 (Metadata only) | \-             |
| MPEG-1 Audio layer 3 V ID3 v2 (Metadata only) | \-             |
| MPEG-1 Video V 2 (File ID only)               | \-             |
| MPEG-1 Video V 3 (File ID only)               | \-             |
| MPEG-2 Audio (File ID only)                   | \-             |
| MPEG-4 (Metadata only)                        | \-             |
| MPEG-7 (Metadata only)                        | \-             |
| QuickTime (Metadata only)                     | \-             |
| Windows Media ASF (Metadata only)             | \-             |
| Windows Media DVR-MS (Metadata only)          | \-             |
| Windows Media Audio WMA (Metadata only)       | \-             |
| Windows Media Playlist (File ID only)         | \-             |
| Windows Media Video WMV (Metadata only)       | \-             |
| WAV (Metadata only)                           | \-             |
| Apple HEIF (File ID only)                     | \-             |
| WebM (File ID only)                           | \-             |

#### B.2.7 Other Formats

| Format                                            | Version     |
|:--------------------------------------------------|:------------|
| AOL Messenger (File ID only)                      | 7.3         |
| Microsoft InfoPath (File ID only)                 | 2007        |
| Microsoft Live Messenger (via XML filter)         | 10.0        |
| Microsoft Office Theme files (File ID only        | 2007 - 2019 |
| Microsoft OneNote (text only)                     | 2007 - 2019 |
| Microsoft Project (table view only)               | 98 – 2010   |
| Microsoft Windows Compiled Help (File ID only)    | .chm        |
| Microsoft Windows DLL (File ID only)              | .dll        |
| Microsoft Windows Executable (File ID only)       | .exe.com    |
| Microsoft Windows Explorer Command (File ID only) | .scf        |
| Microsoft Windows Help (File ID only)             | .hlp        |
| Microsoft Windows Shortcut (File ID only)         | .lnk        |
| Trillian Text Log File (via text filter)          | 4.2         |
| Trillian XML Log File (File ID only)              | 4.2         |
| TrueType Font (File ID only)                      | Ttf, ttc    |
| vCalendar                                         | 2.1         |
| vCard                                             | 2.1         |
| Yahoo Messenger                                   | 6.x – 8     |

#### B.2.8 Presentation Formats

These are the presentation file formats that Oracle Text supports for filtering.

| Format                                              | Version                |
|:----------------------------------------------------|:-----------------------|
| Apple iWork Keynote (text and PDF preview)          | 09, 2014, 2020         |
| Harvard Graphics Presentation DOS                   | 3.0                    |
| IBM Lotus Symphony Presentations                    | 1.x                    |
| Kingsoft WPS Presentation                           | 2010                   |
| LibreOffice Impress                                 | 4.x, 5.x, 6.x          |
| Lotus Freelance                                     | 1.0 – Millennium 9.8   |
| Lotus Freelance for OS/3                            | 2                      |
| Lotus Freelance for Windows                         | 95, 97, SmartSuite 9.8 |
| Microsoft PowerPoint for Macintosh                  | 4.0 – 2016, 2019       |
| Microsoft PowerPoint for Windows                    | 3.0 – 2016, 2019       |
| Microsoft PowerPoint for Windows Slideshow          | 2007 – 2019            |
| Microsoft PowerPoint for Windows Template           | 2007 – 2019            |
| Novell Presentations                                | 3.0, 7.0               |
| OpenOffice Impress                                  | 1.1, 3.0, 4.x          |
| Oracle Open Office Impress                          | 3.x                    |
| StarOffice Impress                                  | 5.2 – 9.0              |
| Strict Open XML –Presentation (File ID only)        | 2013, 2019             |
| WordPerfect Presentations                           | 5.1 – X7               |
| Advanced Function Presentation (AFP) (File ID only) | \-                     |

#### B.2.9 Spreadsheet Formats

These are the spreadsheet file formats that Oracle Text supports for filtering.

| Format                                     | Version                |
|:-------------------------------------------|:-----------------------|
| Apple iWork Numbers (text and PDF preview) | 09                     |
| Apple iWork Numbers ( File ID only)        | 2014, 2020             |
| Enable Spreadsheet                         | 3.0 – 4.5              |
| First Choice SS                            | Through 3.0            |
| Framework SS                               | 3.0                    |
| IBM Lotus Symphony Spreadsheets            | 1.x                    |
| Kingsoft WPS Spreadsheets                  | 2010                   |
| LibreOffice Calc                           | 4.x                    |
| Lotus 1-2-3                                | Through Millennium 9.8 |
| Lotus 1-2-3 Charts for DOS and Windows     | Through 5.0            |
| Lotus 1-2-3 for OS/2                       | 2.0                    |
| Microsoft Excel Charts                     | 2.x – 2007             |
| Microsoft Excel for Macintosh              | 98 – 2011              |
| Microsoft Excel for Windows                | 3.0 – 2019             |
| Microsoft Excel for Windows (text only)    | 2003 XML               |
| Microsoft Excel for Windows (.xlsb)        | 2007 – 2019 (Binary)   |
| Microsoft Works SS for DOS                 | 2.0                    |
| Microsoft Works SS for Macintosh           | 2.0                    |
| Microsoft Works SS for Windows             | 3.0, 4.0               |
| Multiplan                                  | 4.0                    |
| Novell PerfectWorks Spreadsheet            | 2.0                    |
| OpenOffice Calc                            | 1.1 – 3.0              |
| Oracle Open Office Calc                    | 3.x                    |
| PFS: Plan                                  | 1.0                    |
| Quattro Pro for DOS                        | Through 5.0            |
| Quattro Pro for Windows                    | Through X7             |
| SmartWare Spreadsheet                      | \-                     |
| SmartWare II SS                            | 1.02                   |
| StarOffice Calc                            | 5.2 – 9.0              |
| SuperCalc                                  | 5.0                    |
| Symphony                                   | Through 2.0            |
| VP-Planner                                 | 1.0                    |

#### B.2.10 Text and Markup Formats

These are the formats for text and markup versions of documents that Oracle Text supports.

| Format                                                                                    | Version                                |
|:------------------------------------------------------------------------------------------|:---------------------------------------|
| ANSI Text                                                                                 | 7 and 8 bit                            |
| ASCII Text                                                                                | 7 and 8 bit                            |
| Ami Pro for OS2                                                                           | \-                                     |
| Ami Pro for Windows                                                                       | 2.0, 3.0                               |
| Apple iWork Pages (text and PDF preview)                                                  | 09                                     |
| Apple iWork Pages (File ID only)                                                          | 2014, 2020                             |
| DEC DX                                                                                    | Through 4.0                            |
| DEC DX Plus                                                                               | 4.0, 4.1                               |
| Enable Word Processor                                                                     | 3.0 – 4.5                              |
| First Choice WP                                                                           | 1.0, 3.0                               |
| Framework WP                                                                              | 3.0                                    |
| Hangul                                                                                    | 97 – 2010                              |
| IBM DCA/FFT                                                                               | \-                                     |
| IBM DisplayWrite                                                                          | 2.0 – 5.0                              |
| IBM Writing Assistant                                                                     | 1.01                                   |
| Ichitaro                                                                                  | 5.0, 6.0, 8.0 – 13.0, 2004, 2010, 2013 |
| JustWrite                                                                                 | Through 3.0                            |
| Kingsoft WPS Writer                                                                       | 2010                                   |
| Legacy                                                                                    | 1.1                                    |
| LibreOffice Writer                                                                        | 4.x                                    |
| Lotus Manuscript                                                                          | Through 2.0                            |
| Lotus WordPro (text only)                                                                 | 9.7, 96 – Millennium 9.8               |
| MacWrite II                                                                               | 1.1                                    |
| Mass 11                                                                                   | Through 8.0                            |
| Microsoft Publisher (File ID only)                                                        | 2003 - 2016                            |
| Microsoft Word for DOS                                                                    | 4.0 – 6.0                              |
| Microsoft Word for Macintosh                                                              | 4.0 – 6.0, 98 – 2011                   |
| Microsoft Word for Windows                                                                | 1.0 – 2016, 2019                       |
| Microsoft Word for Windows (text only)                                                    | 2003 XML                               |
| DOS character set                                                                         | \-                                     |
| EBCDIC                                                                                    | \-                                     |
| HTML (HTML5 advanced elements are limited to those typically found in HTML based emails.) | 1.0 – 5.0                              |
| IBM DCA/RFT                                                                               | \-                                     |
| Macintosh character set                                                                   | \-                                     |
| Rich Text Format (RTF)                                                                    | \-                                     |
| Unicode Text                                                                              | 3.0, 4.0                               |
| UTF-8                                                                                     | \-                                     |
| Wireless Markup Language                                                                  | \-                                     |
| XML (Text only)                                                                           | \-                                     |
| XHTML (File ID only)                                                                      | 1.0                                    |
| XML Localization Interchange File Format (File ID only)                                   | \-                                     |
| XML Forms Data Format (File ID only)                                                      | \-                                     |

#### B.2.11 Word Processing and Desktop Publishing Formats

These are the formats for word processing and desktop publishing handled by Oracle Text filters.

| Format                                                | Version                          |
|:------------------------------------------------------|:---------------------------------|
| Adobe FrameMaker (MIF only)                           | 3.0 – 6.0                        |
| Adobe Illustrator Postscript                          | Level 2                          |
| Ami                                                   | \-                               |
| Ami Pro for OS2                                       | \-                               |
| Ami Pro for Windows                                   | 2.0, 3.0                         |
| Apple iWork Pages (Text and PDF preview)              | 09                               |
| Apple iWork Pages (File ID only)                      | 2014, 2020                       |
| DEC DX                                                | Through 4.0                      |
| DEC DX Plus                                           | 4.0, 4.1                         |
| Enable Word Processor                                 | 3.0 – 4.5                        |
| First Choice WP                                       | 1.0, 3.0                         |
| Framework WP                                          | 3.0                              |
| Hangul                                                | 97 – 2010                        |
| IBM DCA/FFT                                           | \-                               |
| IBM DisplayWrite                                      | 2.0 – 5.0                        |
| IBM Writing Assistant                                 | 1.01                             |
| Ichitaro                                              | 5.0, 6.0, 8.0 – 13.0, 2004, 2013 |
| JustWrite                                             | Through 3.0                      |
| Kingsoft WPS Writer                                   | 2010                             |
| Legacy                                                | 1.1                              |
| LibreOffice Writer                                    | 4.x                              |
| Lotus Manuscript                                      | Through 2.0                      |
| Lotus WordPro (text only)                             | 9.7, 96 – Millennium 9.8         |
| MacWrite II                                           | 1.1                              |
| Mass 11                                               | Through 8.0                      |
| Microsoft Word for DOS                                | 4.0 – 6.0                        |
| Microsoft Word for Macintosh                          | 4.0 – 6.0, 98 – 2011             |
| Microsoft Word for Windows                            | 1.0 – 2016, 2019                 |
| Microsoft Word for Windows (text only via XML filter) | 2003 XML                         |
| Microsoft Word for Windows                            | 98-J                             |
| Microsoft WordPad                                     | \-                               |
| Microsoft Works WP for DOS                            | 2.0                              |
| Microsoft Works WP for Macintosh                      | 2.0                              |
| Microsoft Works WP for Windows                        | 3.0, 4.0                         |
| Microsoft Write for Windows                           | 1.0 – 3.0                        |
| MultiMate                                             | Through 4.0                      |
| MultiMate Advantage                                   | 2.0                              |
| Navy DIF                                              | \-                               |
| Nota Bene                                             | 3.0                              |
| Novell PerfectWorks Word Processor                    | 2.0                              |
| OfficeWriter                                          | 4.0 – 6.0                        |
| OpenOffice Writer                                     | 1.1 – 3.0                        |
| Oracle Open Office Writer                             | 3.x                              |
| PC File Doc                                           | 5.0                              |
| PFS: Write                                            | A, B                             |
| Professional Write for DOS                            | 1.0, 2.0                         |
| Professional Write Plus for Windows                   | 1.0                              |
| Q&A Write                                             | 2.0, 3.0                         |
| Samna Word IV                                         | 1.0 – 3.0                        |
| Samna Word IV+                                        | \-                               |
| Signature                                             | 1.0                              |
| SmartWare II WP                                       | 1.02                             |
| Sprint                                                | 1.0                              |
| StarOffice Writer                                     | 5.2 – 9.0                        |
| Strict Open XML –Document (file ID only)              | 2013, 2016, 2019                 |
| Total Word                                            | 1.2                              |
| Wang IWP                                              | Through 2.6                      |
| WordMarc Composer                                     | \-                               |
| WordMarc Composer+                                    | \-                               |
| WordMarc Word Processor                               | \-                               |
| WordPerfect for DOS                                   | 4.2                              |
| WordPerfect for Macintosh                             | 1.02 – 3.1                       |
| WordPerfect for Windows                               | 5.1 – X7                         |
| WordStar 2000 for DOS                                 | 1.0 – 3.0                        |
| Wordstar for DOS                                      | 3.0 – 7.0                        |
| Wordstar for Windows                                  | 1.0                              |
| XyWrite                                               | Through III+                     |

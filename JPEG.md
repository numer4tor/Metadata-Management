# JPEG Metadata Management
Manage metadata for JPEG pictures

- [JPEG Metadata Management](#jpeg-metadata-management)
  - [Timestamp format](#timestamp-format)
  - [Windows File Explorer](#windows-file-explorer)
  - [Zoner Photo Studio X](#zoner-photo-studio-x)


## Timestamp format
Some information to timestamp format:

| Metadata                                     | Format                    |
| -------------------------------------------- | ------------------------- |
| File:System:Time:File Modification Date/Time | 9999:99:99 99:99:99+99:99 |
| File:System:Time:File Access Date/Time       | 9999:99:99 99:99:99+99:99 |
| File:System:Time:File Creation Date/Time     | 9999:99:99 99:99:99+99:99 |
| EXIF:ExifIFD:Time:Date/Time Original         | 9999:99:99 99:99:99       |
| EXIF:ExifIFD:Time:Create Date                | 9999:99:99 99:99:99       |
| EXIF:ExifIFD:Time:Offset Time                | +99:99                    |
| EXIF:ExifIFD:Time:Offset Time Original       | +99:99                    |
| XMP:XMP-microsoft:Time:Date Acquired         | 9999:99:99 99:99:99.999   |


## Windows File Explorer
The mapping from the Windows Fileexplorer to the JPEG metadata is as follows:

| Category                     | Field                        | Metadata Field                                                                                                                   |
| ---------------------------- | ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| Beschreibung                 | Titel                        | EXIF:IFD0:Image:Image Description <br/> EXIF:IFD0:Image:XP Title <br/> XMP:XMP-dc:Image:Title <br/> XMP:XMP-dc:Image:Description |
| Beschreibung                 | Betreff                      | EXIF:IFD0:Image:XP Keywords <br/> EXIF:IFD0:Image:XP Subject <br/> XMP:XMP-microsoft:Image:Last Keyword XMP                      |
| Beschreibung                 | Bewertung                    | XMP:XMP-xmp:Image:Rating <br/> XMP:XMP-microsoft:Image:Rating Percent                                                            |
| Beschreibung                 | Markierungen                 | EXIF:IFD0:Image:XP Keywords <br/> XMP:XMP-dc:Image:Subject <br/> XMP:XMP-microsoft:Image:Last Keyword XMP                        |
| Beschreibung                 | Kommentare                   | EXIF:IFD0:Image:XP Comment                                                                                                       |
| Ursprung                     | Autoren                      | EXIF:IFD0:Author:Artist <br/> EXIF:IFD0:Author:XP Author <br/> XMP:XMP-dc:Author:Creator                                         |
| Ursprung                     | Aufnahmedatum                | EXIF:ExifIFD:Time:Date/Time Original <br/> EXIF:ExifIFD:Time:Create Date                                                         |
| Ursprung                     | Programmname                 | EXIF:IFD0:Image:Software <br/> EXIF:IFD0:Camera:Camera Model Name                                                                |
| Ursprung                     | Erfassungsdatum              | XMP:XMP-microsoft:Time:Date Acquired                                                                                             |
| Ursprung                     | Copyright                    | EXIF:IFD0:Author:Copyright <br/> XMP:XMP-dc:Author:Rights                                                                        |
| Bild                         | Bild-ID                      | EXIF:ExifIFD:Image:Image Unique ID                                                                                               |
| Bild                         | Abmessungen                  | N/A                                                                                                                              |
| Bild                         | Breite                       | File:Image:Image Width <br/> EXIF:ExifIFD:Image:Exif Image Width                                                                 |
| Bild                         | Höhe                         | File:Image:Image Height <br/> EXIF:ExifIFD:Image:Exif Image Height                                                               |
| Bild                         | Horizontale Auflösung        | N/A                                                                                                                              |
| Bild                         | Vertikale Auflösung          | N/A                                                                                                                              |
| Bild                         | Bittiefe                     | N/A                                                                                                                              |
| Bild                         | Komprimierung                | N/A                                                                                                                              |
| Bild                         | Auflösungseinheit            | N/A                                                                                                                              |
| Bild                         | Farbdarstellung              | EXIF:ExifIFD:Image:Color Space                                                                                                   |
| Bild                         | Komprimierte Bits/Pixel      | N/A                                                                                                                              |
| Kamera                       | Kamerahersteller             | EXIF:IFD0:Camera:Make                                                                                                            |
| Kamera                       | Kameramodell                 | EXIF:IFD0:Camera:Camera Model Name                                                                                               |
| Kamera                       | Blendenzahl                  | EXIF:ExifIFD:Image:F Number <br/> EXIF:ExifIFD:Image:Aperture Value <br/> EXIF:ExifIFD:Camera:Max Aperture Value                 |
| Kamera                       | Belichtungszeit              | EXIF:ExifIFD:Image:Exposure Time                                                                                                 |
| Kamera                       | ISO-Filmempfindlichkeit      | EXIF:ExifIFD:Image:ISO                                                                                                           |
| Kamera                       | Lichtwert                    | EXIF:ExifIFD:Image:Exposure Compensation                                                                                         |
| Kamera                       | Brennweite                   | EXIF:ExifIFD:Camera:Focal Length                                                                                                 |
| Kamera                       | Maximale Blende              | EXIF:ExifIFD:Camera:Max Aperture Value                                                                                           |
| Kamera                       | Messmodus                    | EXIF:ExifIFD:Camera:Exposure Program                                                                                             |
| Kamera                       | Abstand                      | N/A                                                                                                                              |
| Kamera                       | Blitzlichtmodus              | EXIF:ExifIFD:Camera:Flash                                                                                                        |
| Kamera                       | Blitzlichtenergie            | N/A                                                                                                                              |
| Kamera                       | 35mm Brennweite              | EXIF:ExifIFD:Camera:Focal Length In 35mm Format                                                                                  |
| Erweiterte Fotoeigenschaften | Objektivhersteller           | XMP:XMP-microsoft:Image:Lens Manufacturer                                                                                        |
| Erweiterte Fotoeigenschaften | Objektivmodell               | XMP:XMP-microsoft:Image:Lens Model                                                                                               |
| Erweiterte Fotoeigenschaften | Blitzlichthersteller         | XMP:XMP-microsoft:Image:Flash Manufacturer                                                                                       |
| Erweiterte Fotoeigenschaften | Blitzlichtmodell             | XMP:XMP-microsoft:Image:Flash Model                                                                                              |
| Erweiterte Fotoeigenschaften | Seriennummer der Kamera      | XMP:XMP-microsoft:Image:Camera Serial Number                                                                                     |
| Erweiterte Fotoeigenschaften | Kontrast                     | EXIF:ExifIFD:Camera:Contrast                                                                                                     |
| Erweiterte Fotoeigenschaften | Helligkeit                   | N/A                                                                                                                              |
| Erweiterte Fotoeigenschaften | Lichtquelle                  | EXIF:ExifIFD:Camera:Light Source                                                                                                 |
| Erweiterte Fotoeigenschaften | Belichtungsprogramm          | EXIF:ExifIFD:Camera:Exposure Program                                                                                             |
| Erweiterte Fotoeigenschaften | Sättigung                    | EXIF:ExifIFD:Camera:Saturation                                                                                                   |
| Erweiterte Fotoeigenschaften | Schärfe                      | EXIF:ExifIFD:Camera:Sharpness                                                                                                    |
| Erweiterte Fotoeigenschaften | Weissausgleich               | EXIF:ExifIFD:Camera:White Balance                                                                                                |
| Erweiterte Fotoeigenschaften | Fotometrische Interpretation | N/A                                                                                                                              |
| Erweiterte Fotoeigenschaften | Digitalzoom                  | EXIF:ExifIFD:Camera:Digital Zoom Ratio                                                                                           |
| Erweiterte Fotoeigenschaften | EXIF-Version                 | EXIF:ExifIFD:Image:Exif Version                                                                                                  |
| GPS                          | Breitengrad                  | EXIF:GPS:Location:GPS Latitude                                                                                                   |
| GPS                          | Längengrad                   | EXIF:GPS:Location:GPS Longitude                                                                                                  |
| Datei                        | Name                         | File:System:Other:File Name                                                                                                      |
| Datei                        | Elementtyp                   | File:Other:File Type                                                                                                             |
| Datei                        | Dateispeicherort             | N/A                                                                                                                              |
| Datei                        | Erstelldatum                 | File:System:Time:File Creation Date/Time                                                                                         |
| Datei                        | Änderungsdatum               | File:System:Time:File Modification Date/Time                                                                                     |
| Datei                        | Grösse                       | File:System:Other:File Size                                                                                                      |
| Datei                        | Attribute                    | N/A                                                                                                                              |
| Datei                        | Verfügbarkeit                | N/A                                                                                                                              |
| Datei                        | Offlinestatus                | N/A                                                                                                                              |
| Datei                        | Freigegeben für              | N/A                                                                                                                              |
| Datei                        | Besitzer                     | N/A                                                                                                                              |
| Datei                        | Computer                     | N/A                                                                                                                              |


## Zoner Photo Studio X
The mapping from ZPS X to the JPEG metadata is as follows:

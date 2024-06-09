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
| EXIF:IFD0:Time:Modify Date                   | 9999:99:99 99:99:99       |
| IPTC:Time:Date Created                       | 9999:99:99                |
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

| Kategorie         | Field                        | Metadata Field                                                                                       |
| ----------------- | ---------------------------- | ---------------------------------------------------------------------------------------------------- |
| Textinformationen | Name                         | EXIF:IFD0:Image:Image Description <br/> XMP:XMP-dc:Image:Title <br/> IPTC:Other:Object Name          |
| Textinformationen | Autor                        | EXIF:IFD0:Author:Artist <br/> XMP:XMP-dc:Author:Creator <br/> IPTC:Author:By-line                    |
| Textinformationen | Copyright                    | EXIF:IFD0:Author:Copyright <br/> XMP:XMP-dc:Author:Rights <br/> IPTC:Author:Copyright Notice         |
| Textinformationen | Beschreibung                 | EXIF:ExifIFD:Image:User Comment <br/> XMP:XMP-dc:Image:Description <br/> IPTC:Other:Caption-Abstract |
| Textinformationen | Beschreibung - Autor         | XMP:XMP-photoshop:Author:Caption Writer <br/> IPTC:Author:Writer-Editor                              |
| Textinformationen | Farbmarkierung               | XMP:XMP-xmp:Image:Label                                                                              |
| Textinformationen | Bewertung                    | XMP:XMP-xmp:Image:Rating                                                                             |
| Fotoinformationen | Erstellt                     | EXIF:ExifIFD:Time:Date/Time Original <br/> IPTC:Time:Date Created                                    |
| Fotoinformationen | Digitalisiert                | EXIF:ExifIFD:Time:Create Date                                                                        |
| Fotoinformationen | Geändert                     | File:System:Time:File Modification Date/Time <br/> EXIF:IFD0:Time:Modify Date                        |
| Fotoinformationen | Empfindlichkeit              | EXIF:ExifIFD:Image:ISO                                                                               |
| Fotoinformationen | Belichtungszeit              | EXIF:ExifIFD:Image:Exposure Time                                                                     |
| Fotoinformationen | Blende                       | EXIF:ExifIFD:Image:F Number <br/> XMP:XMP-exif:Image:Aperture Value                                  |
| Fotoinformationen | Brennweite                   | EXIF:ExifIFD:Camera:Focal Length                                                                     |
| Fotoinformationen | Brennweite (EQ35mm)          | EXIF:ExifIFD:Camera:Focal Length In 35mm Format                                                      |
| Fotoinformationen | Objektiv                     | EXIF:ExifIFD:Image:Lens Model                                                                        |
| Fotoinformationen | Hersteller des Objektivs     | EXIF:ExifIFD:Image:Lens Make                                                                         |
| Fotoinformationen | Belichtungskorrektur         | EXIF:ExifIFD:Image:Exposure Compensation                                                             |
| Fotoinformationen | Blitz                        | EXIF:ExifIFD:Camera:Flash                                                                            |
| Fotoinformationen | Hersteller der Kamera        | EXIF:IFD0:Camera:Make                                                                                |
| Fotoinformationen | Kameramodell                 | EXIF:IFD0:Camera:Camera Model Name                                                                   |
| Fotoinformationen | Software                     | EXIF:IFD0:Image:Software                                                                             |
| Fotoinformationen | Belichtungsprogramm          | EXIF:ExifIFD:Camera:Exposure Program                                                                 |
| Fotoinformationen | Belichtungsmodus             | EXIF:ExifIFD:Camera:Exposure Mode                                                                    |
| Fotoinformationen | Modus für Belichtungsmessung | EXIF:ExifIFD:Camera:Metering Mode                                                                    |
| Fotoinformationen | Typ der aufgenommenen Szene  | EXIF:ExifIFD:Camera:Scene Capture Type                                                               |
| Fotoinformationen | Weissabgleich                | EXIF:ExifIFD:Camera:White Balance                                                                    |
| Fotoinformationen | Blitz Detaillierte Info      | N/A                                                                                                  |
| Fotoinformationen | Transformation               | N/A                                                                                                  |
| Fotoinformationen | Maximale Blendenöffnung      | EXIF:ExifIFD:Camera:Max Aperture Value                                                               |
| Fotoinformationen | Digital-Zoom-Verhältnis      | EXIF:ExifIFD:Camera:Digital Zoom Ratio                                                               |
| Fotoinformationen | Geographische Breite         | EXIF:GPS:Location:GPS Latitude                                                                       |
| Fotoinformationen | Geographische Länge          | EXIF:GPS:Location:GPS Longitude                                                                      |
| Fotoinformationen | Farbraum                     | EXIF:ExifIFD:Image:Color Space                                                                       |
| Fotoinformationen | Farbmodell                   | File:Image:Y Cb Cr Sub Sampling                                                                      |
| Fotoinformationen | Komprimierung                | File:Other:File Type                                                                                 |
| Fotoinformationen | Auflösung                    | N/A                                                                                                  |
| Fotoinformationen | Eindeutige Bild-ID           | EXIF:ExifIFD:Image:Image Unique ID                                                                   |
| Fotoinformationen | Digitale Unterschrift        | N/A                                                                                                  |
| Fotoinformationen | Dynamikumfang                | N/A                                                                                                  |
| Fotoinformationen | Primärfarben                 | N/A                                                                                                  |
| Fotoinformationen | Weisspunkt                   | N/A                                                                                                  |
| Fotoinformationen | Übertragungscharakteristik   | N/A                                                                                                  |
| Schlüsselwörter   | Gewählte Schlüsselwörter     | XMP:XMP-dc:Image:Subject <br/> IPTC:Other:Keywords                                                   |
| Bildquellen       | Verdienste                   | IPTC:Author:Credit                                                                                   |
| Bildquellen       | Quelle                       | IPTC:Author:Source                                                                                   |
| Bildquellen       | Kopfzeile                    | IPTC:Other:Headline                                                                                  |
| Bildquellen       | Anweisungen                  | XMP:XMP-photoshop:Image:Instructions <br/> IPTC:Other:Special Instructions                           |
| Bildquellen       | Verweis zu Ursprung          | XMP:XMP-photoshop:Image:Transmission Reference <br/> IPTC:Other:Original Transmission Reference      |
| Bildquellen       | Dringlichkeit                | IPTC:Other:Urgency                                                                                   |
| Benutzerinfo      | Name in Fremdsprache         | XMP:XMP-znr:Unknown:International Title                                                              |
| Benutzerinfo      | Beschreibung in Fremdsprache | XMP:XMP-znr:Unknown:International Description                                                        |
| Benutzerinfo      | Veröffentlicht in            | XMP:XMP-znr:Unknown:Published In                                                                     |
| Benutzerinfo      | Stativ                       | XMP:XMP-znr:Unknown:Tripod                                                                           |
| Benutzerinfo      | Filter                       | XMP:XMP-znr:Unknown:Filter                                                                           |
| Benutzerinfo      | Zwischenriing                | XMP:XMP-znr:Unknown:Mezikrouzek                                                                      |
| Benutzerinfo      | Film                         | XMP:XMP-znr:Unknown:Film                                                                             |
| Benutzerinfo      | Filmbeschriftung im Archiv   | XMP:XMP-znr:Unknown:Film Archive Label                                                               |
| Benutzerinfo      | Format                       | XMP:XMP-znr:Unknown:Film Format                                                                      |
| Benutzerinfo      | Verwendung                   | XMP:XMP-znr:Unknown:Use                                                                              |


## Synology Photos
The mapping from the JPEG metadata to the Syonology Photos metadata is as follows (see also [this article](https://kb.synology.com/en-uk/DSM/tutorial/What_metadata_standards_does_Synology_Photos_support)):

| Synology Photos Field | Metadata Field                                                                                                                                                                                |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Description           | EXIF:IFD0:Image:Image Description                                                                                                                                                             |
| Rating                | 1. EXIF:IFD0:Image:Rating <br/> 2. EXIF:IFD0:Image:Rating Percent <br/> 3. XMP:XMP-xmp:Image:Rating <br/> 4. XMP:XMP-xmp:Image:Rating Percent <br/> 5. XMP:XMP-microsoft:Image:Rating Percent |
| Date Taken            | 1. EXIF:ExifIFD:Time:Date/Time Original <br/> 2.                                                                                                                                              |
| Geolocation           |                                                                                                                                                                                               |
| Camera                |                                                                                                                                                                                               |
| Tags                  | 1. XMP:XMP-dc:Image:Subject <br/> 2. IPTC:Other:Keywords                                                                                                                                      |

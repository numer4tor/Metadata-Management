# JPEG
Manage metadata for JPEG pictures

- [JPEG](#jpeg)
  - [Timestamp format](#timestamp-format)
  - [Windows File Explorer](#windows-file-explorer)
  - [Zoner Photo Studio X](#zoner-photo-studio-x)
    - [Mapping from Windows Explorer](#mapping-from-windows-explorer)
  - [Synology Photos](#synology-photos)
    - [Information](#information)
    - [More](#more)
    - [Problems](#problems)


## Timestamp format
Some information to timestamp format:

| Metadata                             | Format                    |
| ------------------------------------ | ------------------------- |
| File:System:Time:FileModifyDate      | 9999:99:99 99:99:99+99:99 |
| File:System:Time:FileAccessDate      | 9999:99:99 99:99:99+99:99 |
| File:System:Time:FileCreateDate      | 9999:99:99 99:99:99+99:99 |
| EXIF:ExifIFD:Time:DateTimeOriginal   | 9999:99:99 99:99:99       |
| EXIF:ExifIFD:Time:CreateDate         | 9999:99:99 99:99:99       |
| EXIF:ExifIFD:Time:OffsetTime         | +99:99                    |
| EXIF:ExifIFD:Time:OffsetTimeOriginal | +99:99                    |
| EXIF:IFD0:Time:ModifyDate            | 9999:99:99 99:99:99       |
| IPTC:Time:DateCreated                | 9999:99:99                |
| XMP:XMP-microsoft:Time:DateAcquired  | 9999:99:99 99:99:99.999   |


## Windows File Explorer
The mapping from the Windows Fileexplorer to the JPEG metadata is as follows:

| Category                     | Field                        | Metadata Field                                                                                                                 |
| ---------------------------- | ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Beschreibung                 | Titel                        | EXIF:IFD0:Image:ImageDescription <br/> EXIF:IFD0:Image:XPTitle <br/> XMP:XMP-dc:Image:Title <br/> XMP:XMP-dc:Image:Description |
| Beschreibung                 | Betreff                      | EXIF:IFD0:Image:XPKeywords <br/> EXIF:IFD0:Image:XPSubject <br/> XMP:XMP-microsoft:Image:LastKeywordXMP                        |
| Beschreibung                 | Bewertung                    | XMP:XMP-xmp:Image:Rating <br/> XMP:XMP-microsoft:Image:RatingPercent                                                           |
| Beschreibung                 | Markierungen                 | EXIF:IFD0:Image:XPKeywords <br/> XMP:XMP-dc:Image:Subject <br/> XMP:XMP-microsoft:Image:LastKeywordXMP                         |
| Beschreibung                 | Kommentare                   | EXIF:IFD0:Image:XPComment                                                                                                      |
| Ursprung                     | Autoren                      | EXIF:IFD0:Author:Artist <br/> EXIF:IFD0:Author:XPAuthor <br/> XMP:XMP-dc:Author:Creator                                        |
| Ursprung                     | Aufnahmedatum                | EXIF:ExifIFD:Time:DateTimeOriginal <br/> EXIF:ExifIFD:Time:CreateDate                                                          |
| Ursprung                     | Programmname                 | EXIF:IFD0:Image:Software <br/> EXIF:IFD0:Camera:CameraModelName                                                                |
| Ursprung                     | Erfassungsdatum              | XMP:XMP-microsoft:Time:DateAcquired                                                                                            |
| Ursprung                     | Copyright                    | EXIF:IFD0:Author:Copyright <br/> XMP:XMP-dc:Author:Rights                                                                      |
| Bild                         | Bild-ID                      | EXIF:ExifIFD:Image:ImageUniqueID                                                                                               |
| Bild                         | Abmessungen                  | N/A                                                                                                                            |
| Bild                         | Breite                       | File:Image:ImageWidth <br/> EXIF:ExifIFD:Image:ExifImageWidth                                                                  |
| Bild                         | Höhe                         | File:Image:ImageHeight <br/> EXIF:ExifIFD:Image:ExifImageHeight                                                                |
| Bild                         | Horizontale Auflösung        | N/A                                                                                                                            |
| Bild                         | Vertikale Auflösung          | N/A                                                                                                                            |
| Bild                         | Bittiefe                     | N/A                                                                                                                            |
| Bild                         | Komprimierung                | N/A                                                                                                                            |
| Bild                         | Auflösungseinheit            | N/A                                                                                                                            |
| Bild                         | Farbdarstellung              | EXIF:ExifIFD:Image:ColorSpace                                                                                                  |
| Bild                         | Komprimierte Bits/Pixel      | N/A                                                                                                                            |
| Kamera                       | Kamerahersteller             | EXIF:IFD0:Camera:Make                                                                                                          |
| Kamera                       | Kameramodell                 | EXIF:IFD0:Camera:CameraModelName                                                                                               |
| Kamera                       | Blendenzahl                  | EXIF:ExifIFD:Image:FNumber <br/> EXIF:ExifIFD:Image:ApertureValue <br/> EXIF:ExifIFD:Camera:MaxApertureValue                   |
| Kamera                       | Belichtungszeit              | EXIF:ExifIFD:Image:ExposureTime                                                                                                |
| Kamera                       | ISO-Filmempfindlichkeit      | EXIF:ExifIFD:Image:ISO                                                                                                         |
| Kamera                       | Lichtwert                    | EXIF:ExifIFD:Image:ExposureCompensation                                                                                        |
| Kamera                       | Brennweite                   | EXIF:ExifIFD:Camera:FocalLength                                                                                                |
| Kamera                       | Maximale Blende              | EXIF:ExifIFD:Camera:MaxApertureValue                                                                                           |
| Kamera                       | Messmodus                    | EXIF:ExifIFD:Camera:ExposureProgram                                                                                            |
| Kamera                       | Abstand                      | N/A                                                                                                                            |
| Kamera                       | Blitzlichtmodus              | EXIF:ExifIFD:Camera:Flash                                                                                                      |
| Kamera                       | Blitzlichtenergie            | N/A                                                                                                                            |
| Kamera                       | 35mm Brennweite              | EXIF:ExifIFD:Camera:FocalLengthIn35mmFormat                                                                                    |
| Erweiterte Fotoeigenschaften | Objektivhersteller           | XMP:XMP-microsoft:Image:LensManufacturer                                                                                       |
| Erweiterte Fotoeigenschaften | Objektivmodell               | XMP:XMP-microsoft:Image:LensModel                                                                                              |
| Erweiterte Fotoeigenschaften | Blitzlichthersteller         | XMP:XMP-microsoft:Image:FlashManufacturer                                                                                      |
| Erweiterte Fotoeigenschaften | Blitzlichtmodell             | XMP:XMP-microsoft:Image:FlashModel                                                                                             |
| Erweiterte Fotoeigenschaften | Seriennummer der Kamera      | XMP:XMP-microsoft:Image:CameraSerialNumber                                                                                     |
| Erweiterte Fotoeigenschaften | Kontrast                     | EXIF:ExifIFD:Camera:Contrast                                                                                                   |
| Erweiterte Fotoeigenschaften | Helligkeit                   | N/A                                                                                                                            |
| Erweiterte Fotoeigenschaften | Lichtquelle                  | EXIF:ExifIFD:Camera:LightSource                                                                                                |
| Erweiterte Fotoeigenschaften | Belichtungsprogramm          | EXIF:ExifIFD:Camera:ExposureProgram                                                                                            |
| Erweiterte Fotoeigenschaften | Sättigung                    | EXIF:ExifIFD:Camera:Saturation                                                                                                 |
| Erweiterte Fotoeigenschaften | Schärfe                      | EXIF:ExifIFD:Camera:Sharpness                                                                                                  |
| Erweiterte Fotoeigenschaften | Weissausgleich               | EXIF:ExifIFD:Camera:WhiteBalance                                                                                               |
| Erweiterte Fotoeigenschaften | Fotometrische Interpretation | N/A                                                                                                                            |
| Erweiterte Fotoeigenschaften | Digitalzoom                  | EXIF:ExifIFD:Camera:DigitalZoomRatio                                                                                           |
| Erweiterte Fotoeigenschaften | EXIF-Version                 | EXIF:ExifIFD:Image:ExifVersion                                                                                                 |
| GPS                          | Breitengrad                  | EXIF:GPS:Location:GPSLatitude                                                                                                  |
| GPS                          | Längengrad                   | EXIF:GPS:Location:GPSLongitude                                                                                                 |
| Datei                        | Name                         | File:System:Other:FileName                                                                                                     |
| Datei                        | Elementtyp                   | File:Other:FileType                                                                                                            |
| Datei                        | Dateispeicherort             | N/A                                                                                                                            |
| Datei                        | Erstelldatum                 | File:System:Time:FileCreateDate                                                                                                |
| Datei                        | Änderungsdatum               | File:System:Time:FileModifyDate                                                                                                |
| Datei                        | Grösse                       | File:System:Other:FileSize                                                                                                     |
| Datei                        | Attribute                    | N/A                                                                                                                            |
| Datei                        | Verfügbarkeit                | N/A                                                                                                                            |
| Datei                        | Offlinestatus                | N/A                                                                                                                            |
| Datei                        | Freigegeben für              | N/A                                                                                                                            |
| Datei                        | Besitzer                     | N/A                                                                                                                            |
| Datei                        | Computer                     | N/A                                                                                                                            |


## Zoner Photo Studio X
The mapping from ZPS X to the JPEG metadata is as follows:

| Kategorie         | Field                        | Metadata Field                                                                                      |
| ----------------- | ---------------------------- | --------------------------------------------------------------------------------------------------- |
| Textinformationen | Name                         | EXIF:IFD0:Image:ImageDescription <br/> XMP:XMP-dc:Image:Title <br/> IPTC:Other:ObjectName           |
| Textinformationen | Autor                        | EXIF:IFD0:Author:Artist <br/> XMP:XMP-dc:Author:Creator <br/> IPTC:Author:By-line                   |
| Textinformationen | Copyright                    | EXIF:IFD0:Author:Copyright <br/> XMP:XMP-dc:Author:Rights <br/> IPTC:Author:CopyrightNotice         |
| Textinformationen | Beschreibung                 | EXIF:ExifIFD:Image:UserComment <br/> XMP:XMP-dc:Image:Description <br/> IPTC:Other:Caption-Abstract |
| Textinformationen | Beschreibung - Autor         | XMP:XMP-photoshop:Author:CaptionWriter <br/> IPTC:Author:Writer-Editor                              |
| Textinformationen | Farbmarkierung               | XMP:XMP-xmp:Image:Label                                                                             |
| Textinformationen | Bewertung                    | XMP:XMP-xmp:Image:Rating                                                                            |
| Fotoinformationen | Erstellt                     | EXIF:ExifIFD:Time:DateTimeOriginal <br/> IPTC:Time:DateCreated                                      |
| Fotoinformationen | Digitalisiert                | EXIF:ExifIFD:Time:CreateDate                                                                        |
| Fotoinformationen | Geändert                     | File:System:Time:FileModifyDate <br/> EXIF:IFD0:Time:ModifyDate                                     |
| Fotoinformationen | Empfindlichkeit              | EXIF:ExifIFD:Image:ISO                                                                              |
| Fotoinformationen | Belichtungszeit              | EXIF:ExifIFD:Image:ExposureTime                                                                     |
| Fotoinformationen | Blende                       | EXIF:ExifIFD:Image:FNumber <br/> XMP:XMP-exif:Image:ApertureValue                                   |
| Fotoinformationen | Brennweite                   | EXIF:ExifIFD:Camera:FocalLength                                                                     |
| Fotoinformationen | Brennweite (EQ35mm)          | EXIF:ExifIFD:Camera:FocalLengthIn35mmFormat                                                         |
| Fotoinformationen | Objektiv                     | EXIF:ExifIFD:Image:LensModel                                                                        |
| Fotoinformationen | Hersteller des Objektivs     | EXIF:ExifIFD:Image:LensMake                                                                         |
| Fotoinformationen | Belichtungskorrektur         | EXIF:ExifIFD:Image:ExposureCompensation                                                             |
| Fotoinformationen | Blitz                        | EXIF:ExifIFD:Camera:Flash                                                                           |
| Fotoinformationen | Hersteller der Kamera        | EXIF:IFD0:Camera:Make                                                                               |
| Fotoinformationen | Kameramodell                 | EXIF:IFD0:Camera:CameraModelName                                                                    |
| Fotoinformationen | Software                     | EXIF:IFD0:Image:Software                                                                            |
| Fotoinformationen | Belichtungsprogramm          | EXIF:ExifIFD:Camera:ExposureProgram                                                                 |
| Fotoinformationen | Belichtungsmodus             | EXIF:ExifIFD:Camera:ExposureMode                                                                    |
| Fotoinformationen | Modus für Belichtungsmessung | EXIF:ExifIFD:Camera:MeteringMode                                                                    |
| Fotoinformationen | Typ der aufgenommenen Szene  | EXIF:ExifIFD:Camera:Scene CaptureType                                                               |
| Fotoinformationen | Weissabgleich                | EXIF:ExifIFD:Camera:WhiteBalance                                                                    |
| Fotoinformationen | Blitz Detaillierte Info      | N/A                                                                                                 |
| Fotoinformationen | Transformation               | N/A                                                                                                 |
| Fotoinformationen | Maximale Blendenöffnung      | EXIF:ExifIFD:Camera:MaxApertureValue                                                                |
| Fotoinformationen | Digital-Zoom-Verhältnis      | EXIF:ExifIFD:Camera:DigitalZoomRatio                                                                |
| Fotoinformationen | Geographische Breite         | EXIF:GPS:Location:GPSLatitude                                                                       |
| Fotoinformationen | Geographische Länge          | EXIF:GPS:Location:GPSLongitude                                                                      |
| Fotoinformationen | Farbraum                     | EXIF:ExifIFD:Image:ColorSpace                                                                       |
| Fotoinformationen | Farbmodell                   | File:Image:YCbCrSubSampling                                                                         |
| Fotoinformationen | Komprimierung                | File:Other:FileType                                                                                 |
| Fotoinformationen | Auflösung                    | N/A                                                                                                 |
| Fotoinformationen | Eindeutige Bild-ID           | EXIF:ExifIFD:Image:ImageUniqueID                                                                    |
| Fotoinformationen | Digitale Unterschrift        | N/A                                                                                                 |
| Fotoinformationen | Dynamikumfang                | N/A                                                                                                 |
| Fotoinformationen | Primärfarben                 | N/A                                                                                                 |
| Fotoinformationen | Weisspunkt                   | N/A                                                                                                 |
| Fotoinformationen | Übertragungscharakteristik   | N/A                                                                                                 |
| Schlüsselwörter   | Gewählte Schlüsselwörter     | XMP:XMP-dc:Image:Subject <br/> IPTC:Other:Keywords                                                  |
| Bildquellen       | Verdienste                   | IPTC:Author:Credit                                                                                  |
| Bildquellen       | Quelle                       | IPTC:Author:Source                                                                                  |
| Bildquellen       | Kopfzeile                    | IPTC:Other:Headline                                                                                 |
| Bildquellen       | Anweisungen                  | XMP:XMP-photoshop:Image:Instructions <br/> IPTC:Other:SpecialInstructions                           |
| Bildquellen       | Verweis zu Ursprung          | XMP:XMP-photoshop:Image:TransmissionReference <br/> IPTC:Other:OriginalTransmissionReference        |
| Bildquellen       | Dringlichkeit                | IPTC:Other:Urgency                                                                                  |
| Benutzerinfo      | Name in Fremdsprache         | XMP:XMP-znr:Unknown:InternationalTitle                                                              |
| Benutzerinfo      | Beschreibung in Fremdsprache | XMP:XMP-znr:Unknown:InternationalDescription                                                        |
| Benutzerinfo      | Veröffentlicht in            | XMP:XMP-znr:Unknown:PublishedIn                                                                     |
| Benutzerinfo      | Stativ                       | XMP:XMP-znr:Unknown:Tripod                                                                          |
| Benutzerinfo      | Filter                       | XMP:XMP-znr:Unknown:Filter                                                                          |
| Benutzerinfo      | Zwischenriing                | XMP:XMP-znr:Unknown:Mezikrouzek                                                                     |
| Benutzerinfo      | Film                         | XMP:XMP-znr:Unknown:Film                                                                            |
| Benutzerinfo      | Filmbeschriftung im Archiv   | XMP:XMP-znr:Unknown:FilmArchiveLabel                                                                |
| Benutzerinfo      | Format                       | XMP:XMP-znr:Unknown:FilmFormat                                                                      |
| Benutzerinfo      | Verwendung                   | XMP:XMP-znr:Unknown:Use                                                                             |


### Mapping from Windows Explorer
The mapping from the Windows Fileexplorer to the JPEG metadata available in ZPS X is as follows:

| Windows Category             | Windows Field                | ZPS Category      | ZPS Field                    |
| ---------------------------- | ---------------------------- | ----------------- | ---------------------------- |
| Beschreibung                 | Titel                        | Textinformationen | Name <br/> Beschreibung      |
| Beschreibung                 | Betreff                      |                   |                              |
| Beschreibung                 | Bewertung                    | Textinformationen | Bewertung                    |
| Beschreibung                 | Markierungen                 | Schlüsselwörter   | Gewählte Schlüsselwörter     |
| Beschreibung                 | Kommentare                   |                   |                              |
| Ursprung                     | Autoren                      | Textinformationen | Autoren                      |
| Ursprung                     | Aufnahmedatum                | Fotoinformationen | Erstellt <br/> Digitalisiert |
| Ursprung                     | Programmname                 | Fotoinformationen | Software                     |
| Ursprung                     | Erfassungsdatum              |                   |                              |
| Ursprung                     | Copyright                    | Textinformationen | Copyright                    |
| Bild                         | Bild-ID                      |                   |                              |
| Bild                         | Abmessungen                  |                   |                              |
| Bild                         | Breite                       |                   |                              |
| Bild                         | Höhe                         |                   |                              |
| Bild                         | Horizontale Auflösung        | Fotoinformationen | Auflösung                    |
| Bild                         | Vertikale Auflösung          | Fotoinformationen | Auflösung                    |
| Bild                         | Bittiefe                     |                   |                              |
| Bild                         | Komprimierung                |                   |                              |
| Bild                         | Auflösungseinheit            |                   |                              |
| Bild                         | Farbdarstellung              | Fotoinformationen | Farbraum                     |
| Bild                         | Komprimierte Bits/Pixel      |                   |                              |
| Kamera                       | Kamerahersteller             | Fotoinformationen | Hersteller der Kamera        |
| Kamera                       | Kameramodell                 | Fotoinformationen | Kameramodell                 |
| Kamera                       | Blendenzahl                  | Fotoinformationen | Blendenzahl                  |
| Kamera                       | Belichtungszeit              | Fotoinformationen | Belichtungszeit              |
| Kamera                       | ISO-Filmempfindlichkeit      | Fotoinformationen | Empfindlichkeit              |
| Kamera                       | Lichtwert                    |                   |                              |
| Kamera                       | Brennweite                   | Fotoinformationen | Brennweite                   |
| Kamera                       | Maximale Blende              |                   |                              |
| Kamera                       | Messmodus                    |                   |                              |
| Kamera                       | Abstand                      |                   |                              |
| Kamera                       | Blitzlichtmodus              | Fotoinformationen | Blitz Detaillierte Info      |
| Kamera                       | Blitzlichtenergie            |                   |                              |
| Kamera                       | 35mm Brennweite              | Fotoinformationen | Brennweite (EQ 35mm)         |
| Erweiterte Fotoeigenschaften | Objektivhersteller           |                   |                              |
| Erweiterte Fotoeigenschaften | Objektivmodell               |                   |                              |
| Erweiterte Fotoeigenschaften | Blitzlichthersteller         |                   |                              |
| Erweiterte Fotoeigenschaften | Blitzlichtmodell             |                   |                              |
| Erweiterte Fotoeigenschaften | Seriennummer der Kamera      |                   |                              |
| Erweiterte Fotoeigenschaften | Kontrast                     | Fotoinformationen | Kontrast                     |
| Erweiterte Fotoeigenschaften | Helligkeit                   |                   |                              |
| Erweiterte Fotoeigenschaften | Lichtquelle                  | Fotoinformationen | Lichtquelle                  |
| Erweiterte Fotoeigenschaften | Belichtungsprogramm          | Fotoinformationen | Belichtungsprogramm          |
| Erweiterte Fotoeigenschaften | Sättigung                    | Fotoinformationen | Sättigung                    |
| Erweiterte Fotoeigenschaften | Schärfe                      | Fotoinformationen | Schärfe                      |
| Erweiterte Fotoeigenschaften | Weissausgleich               | Fotoinformationen | Weissabgleich                |
| Erweiterte Fotoeigenschaften | Fotometrische Interpretation |                   |                              |
| Erweiterte Fotoeigenschaften | Digitalzoom                  |                   |                              |
| Erweiterte Fotoeigenschaften | EXIF-Version                 |                   |                              |
| GPS                          | Breitengrad                  | Fotoinformationen | Geographische Breite         |
| GPS                          | Längengrad                   | Fotoinformationen | Geographische Länge          |
| GPS                          | Höhe über Normal-Null        | Fotoinformationen | Höhe über dem Meeresspiegel  |
| Datei                        | Name                         | Fotoinformationen |                              |
| Datei                        | Elementtyp                   |                   |                              |
| Datei                        | Dateispeicherort             |                   |                              |
| Datei                        | Erstelldatum                 |                   |                              |
| Datei                        | Änderungsdatum               |                   |                              |
| Datei                        | Grösse                       |                   |                              |
| Datei                        | Attribute                    |                   |                              |
| Datei                        | Verfügbarkeit                |                   |                              |
| Datei                        | Offlinestatus                |                   |                              |
| Datei                        | Freigegeben für              |                   |                              |
| Datei                        | Besitzer                     |                   |                              |
| Datei                        | Computer                     |                   |                              |


## Synology Photos

### Information
The mapping from the JPEG metadata to the Syonology Photos metadata in the tab Information is as follows (see also [this article](https://kb.synology.com/en-uk/DSM/tutorial/What_metadata_standards_does_Synology_Photos_support)):

| Synology Photos Field | Metadata Field                                                                                                                                                                                                   |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Description           | EXIF:IFD0:Image:ImageDescription                                                                                                                                                                                |
| Rating                | 1. EXIF:IFD0:Image:Rating <br/> 2. EXIF:IFD0:Image:RatingPercent <br/> 3. XMP:XMP-xmp:Image:Rating <br/> 4. XMP:XMP-xmp:Image:RatingPercent <br/> 5. XMP:XMP-microsoft:Image:RatingPercent                       |
| Date Taken            | 1. EXIF:ExifIFD:Time:DateTimeOriginal <br/> 2. EXIF:ExifIFD:Time:CreateDate <br/> 3. EXIF:IFD0:Time:ModifyDate <br/> 4. File:System:Time:FileModifyDate                                                          |
| Geolocation           | Composite:Location:GPSPosition                                                                                                                                                                                   |
| Camera                | A combination of <br/> - EXIF:IFD0:Camera:CameraModelName <br> - EXIF:ExifIFD:Image:ApertureValue <br/> - EXIF:ExifIFD:Image:ExposureTime <br/> - EXIF:ExifIFD:Camera:FocalLength <br/> - EXIF:ExifIFD:Image:ISO |
| Tags                  | 1. XMP:XMP-dc:Image:Subject <br/> 2. IPTC:Other:Keywords                                                                                                                                                         |

### More
The mapping from the JPEG metadata to the Syonology Photos metadata in the tab More is as follows:

| Synology Photos Field      | Metadata Field                               |
| -------------------------- | -------------------------------------------- |
| Aperture                   | EXIF:ExifIFD:Image:ApertureValue             |
| Artist                     | EXIF:IFD0:Author:Artist                      |
| By-line                    | IPTC:Author:By-line                          |
| Caption                    | IPTC:Other:Caption-Abstract                  |
| Caption Writer             | XMP:XMP-photoshop:Author:CaptionWriter       |
| Character Set              | IPTC:Other:CodedCharacterSet                 |
| Color Space                | EXIF:ExifIFD:Image:ColorSpace                |
| Compression                | EXIF:IFD0:Image:Compression                  |
| Copyright                  | EXIF:IFD0:Author:Copyright                   |
| Create Date                | EXIF:ExifIFD:Time:CreateDate                 |
| Creator                    | XMP:XMP-dc:Author:Creator                    |
| Credit                     | IPTC:Author:Credit                           |
| Date Created               | IPTC:Time:DateCreated                        |
| Date and Time              | EXIF:IFD0:Time:ModifyDate                    |
| Date and Time (digitized)  | EXIF:ExifIFD:Time:CreateDate                 |
| Date and Time (original)   | EXIF:ExifIFD:Time:DateTimeOriginal           |
| Date and Time Original     | EXIF:ExifIFD:Time:DateTimeOriginal           |
| Description                | XMP:XMP-dc:Image:Description                 |
| Digital Zoom Ratio         | EXIF:ExifIFD:Camera:DigitalZoomRatio         |
| Exif IFD Pointer           |                                              |
| Exif Version               | EXIF:ExifIFD:Image:ExifVersion               |
| Exposure Bias              | EXIF:ExifIFD:Image:ExposureCompensation      |
| Exposure Mode              | EXIF:ExifIFD:Camera:ExposureMode             |
| Exposure Program           | EXIF:ExifIFD:Camera:ExposureProgram          |
| Exposure Time              | EXIF:ExifIFD:Image:ExposureTime              |
| F Number                   | EXIF:ExifIFD:Image:FNumber                   |
| FNumber                    | EXIF:ExifIFD:Image:FNumber                   |
| FilmArchiveLabel           | XMP:XMP-znr:Unknown:FilmArchiveLabel         |
| FilmFormat                 | XMP:XMP-znr:Unknown:FilmFormat               |
| Flash                      | EXIF:ExifIFD:Camera:Flash                    |
| Focal Length               | EXIF:ExifIFD:Camera:FocalLength              |
| Focal Length In 35mm Film  | EXIF:ExifIFD:Camera:FocalLengthIn35mmFormat  |
| GPS Info IFD Pointer       |                                              |
| GPS Latitude               | EXIF:GPS:Location:GPSLatitude                |
| GPS latitude Reference     | EXIF:GPS:Location:GPSLatitudeRef             |
| GPS Longitude              | EXIF:GPS:Location:GPSLongitude               |
| GPS Longitude Reference    | EXIF:GPS:Location:GPSLongitudeRef            |
| Headline                   | IPTC:Other:Headline                          |
| ISO Speed Ratings          | EXIF:ExifIFD:Image:ISO                       |
| Image Description          | EXIF:IFD0:Image:ImageDescription             |
| Image Length               | EXIF:ExifIFD:Image:ExifImageWidth            |
| Image Unique ID            | EXIF:ExifIFD:Image:ImageUniqueID             |
| Image Width                | File:Image:ImageWidth                        |
| Instructions               | XMP:XMP-photoshop:Image:Instructions         |
| InstructionalDescription   | XMP:XMP-znr:Unknown:InternationalDescription |
| InternationalTitle         | XMP:XMP-znr:Unknown:InternationalTitle       |
| Keywords                   | IPTC:Other:Keywords                          |
| Label                      | XMP:XMP-xmp:Image:Label                      |
| Lens Make                  | EXIF:ExifIFD:Image:LensMake                  |
| Lens Model                 | EXIF:ExifIFD:Image:LensModel                 |
| Manufacturer               | EXIF:IFD0:Camera:Make                        |
| Max Aperture Value         | EXIF:ExifIFD:Camera:MaxApertureValue         |
| Metering Mode              | EXIF:ExifIFD:Camera:MeteringMode             |
| Model                      | EXIF:IFD0:Camera:CameraModelName             |
| Model Version              | IPTC:Other:EnvelopeRecordVersion             |
| Object Name                | IPTC:Other:ObjectName                        |
| Offset Time                | EXIF:ExifIFD:Time:OffsetTime                 |
| Offset Time Original       | EXIF:ExifIFD:Time:OffsetTimeOriginal         |
| Orientation                | EXIF:IFD0:Image:Orientation                  |
| Photometric Interpretation | EXIF:IFD0:Image:PhotometricInterpretation    |
| Pixel X Dimension          | EXIF:ExifIFD:Image:ExifImageWidth            |
| Pixel Y Dimension          | EXIF:ExifIFD:Image:ExifImageHeight           |
| Planar Configuration       | EXIF:IFD0:Image:PlanarConfiguration          |
| PublishedIn                | XMP:XMP-znr:Unknown:PublishedIn              |
| Rating                     | XMP:XMP-znr:Unknown:Rating                   |
| Rating Percent             | XMP:XMP-microsoft:Image:RatingPercent        |
| RatingPercent              | XMP:XMP-microsoft:Image:RatingPercent        |
| Record Version             | IPTC:Other:ApplicationRecordVersion          |
| Resolution Unit            | EXIF:IFD0:Image:ResolutionUnit               |
| Rights                     | XMP:XMP-dc:Author:Rights                     |
| Scene Capture Type         | EXIF:ExifIFD:Camera:SceneCaptureType         |
| Shutter speed              | EXIF:ExifIFD:Image:ShutterSpeedValue         |
| Software                   | EXIF:IFD0:Image:Software                     |
| Source                     | IPTC:Author:Source                           |
| Special Instructions       | IPTC:Other:SpecialInstructions               |
| Sub-seconds Time           | EXIF:ExifIFD:Time:SubSecTime                 |
| Sub-seconds Time Digitized | EXIF:ExifIFD:Time:SubSecTimeDigitized        |
| Sub-seconds Time Original  | EXIF:ExifIFD:Time:SubSecTimeOriginal         |
| Subject                    | XMP:XMP-dc:Image:Subject                     |
| Time Created               | IPTC:Time:Time Created                       |
| Title                      | XMP:XMP-dc:Image:Title                       |
| Transmission Reference     | IPTC:Other:OriginalTransmissionReference     |
| Urgency                    | IPTC:Other:Urgency                           |
| White Balance              | EXIF:ExifIFD:Camera:WhiteBalance             |
| Writer                     | IPTC:Author:Writer-Editor                    |
| X-Resolution               | EXIF:IFD0:Image:XResolution                  |
| Y-Resolution               | EXIF:IFD0:Image:YResolution                  |
| YCbCr Positioning          | EXIF:IFD0:Image:YCbCrPositioning             |
| film                       | XMP:XMP-znr:Unknown:Film                     |
| filter                     | XMP:XMP-znr:Unknown:Filter                   |
| mezikrouzek                | XMP:XMP-znr:Unknown:Mezikrouzek              |
| tripod                     | XMP:XMP-znr:Unknown:Tripod                   |
| use                        | XMP:XMP-znr:Unknown:Use                      |

### Problems
- When setting the Tag **EXIF:ExifIFD:Image:UserComment** the register **More** of the photo information cannot display any information of the photo. Therefore I remove this information:  
`.\exiftool.exe -EXIF:ExifIFD:Image:UserComment= FILE`

- Synology Photos does not take account of the **timezone** as it does e.g. for MP4 files. Therefore the ordering with files of other format can be wrong. See [this post](https://community.synology.com/enu/forum/1/post/138615).

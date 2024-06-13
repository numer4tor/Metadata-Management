# MP4 v2 [ISO 14496-14]
Manage metadata for MP4 v2 [ISO 14496-14] videos

- [MP4 v2 \[ISO 14496-14\]](#mp4-v2-iso-14496-14)
  - [Timestamp format](#timestamp-format)
  - [Windows File Explorer](#windows-file-explorer)
  - [Zoner Photo Studio X](#zoner-photo-studio-x)
    - [Mapping to Sidecar file](#mapping-to-sidecar-file)
    - [Mapping from Windows Explorer](#mapping-from-windows-explorer)
  - [Exif-Tool](#exif-tool)
  - [Synology Photos](#synology-photos)
    - [Information](#information)
    - [More](#more)
    - [Time Metadata  Mapping](#time-metadata--mapping)
    - [Set Creation Date](#set-creation-date)
    - [Set GPS](#set-gps)
    - [All in One](#all-in-one)
    - [File Format](#file-format)



## Timestamp format
Some information to timestamp format:

| Metadata                                     | Format                    |
| -------------------------------------------- | ------------------------- |
| File:System:Time:File Modification Date/Time | 9999:99:99 99:99:99+99:99 |
| File:System:Time:File Access Date/Time       | 9999:99:99 99:99:99+99:99 |
| File:System:Time:File Creation Date/Time     | 9999:99:99 99:99:99+99:99 |
| QuickTime:ItemList:Time:Content Create Date  | 9999                      |
| QuickTime:Keys:Time:CreationDate             | 9999:99:99 99:99:99+99:99 |
| QuickTime:Time:Create Date                   | 9999:99:99 99:99:99       |
| QuickTime:Time:Modify Date                   | 9999:99:99 99:99:99       |
| QuickTime:Track1:Time:Track Create Date      | 9999:99:99 99:99:99       |
| QuickTime:Track1:Time:Track Modify Date      | 9999:99:99 99:99:99       |
| QuickTime:Track2:Time:Media Create Date      | 9999:99:99 99:99:99       |
| QuickTime:Track2:Time:Media Modify Date      | 9999:99:99 99:99:99       |
| XMP:XMP-exif:Time:DateTimeOriginal           | 9999:99:99 99:99:99       |
| XMP:XMP-photoshop:Time:DateCreated           | 9999:99:99 99:99:99       |
| XMP:XMP-xmp:Time:CreateDate                  | 9999:99:99 99:99:99.999   |


## Windows File Explorer
The mapping from the Windows Fileexplorer to the MP4 v2 metadata is as follows:

| Category     | Field                    | Metadata Field                                |
| ------------ | ------------------------ | --------------------------------------------- |
| Beschreibung | Titel                    | QuickTime:ItemList:Audio:Title                |
| Beschreibung | Untertitel               | QuickTime:Microsoft:Video:Subtitle            |
| Beschreibung | Bewertung                | QuickTime:Microsoft:Video:Shared User Rating  |
| Beschreibung | Markierung               | QuickTime:Microsoft:Video:Category            |
| Beschreibung | Kommentare               | QuickTime:ItemList:Audio:Comment              |
| Medien       | Mitwirkende Interpreten  | QuickTime:ItemList:Audio:Artist               |
| Medien       | Jahr                     | QuickTime:ItemList:Time:Content Create Date   |
| Medien       | Genre                    | QuickTime:ItemList:Audio:Genre                |
| Ursprung     | Regisseure               | QuickTime:Microsoft:Video:Director            |
| Ursprung     | Produzenten              | QuickTime:Microsoft:Video:Producer            |
| Ursprung     | Texter                   | QuickTime:Microsoft:Author:Writer             |
| Ursprung     | Herausgeber              | QuickTime:Microsoft:Video:Publisher           |
| Ursprung     | Inhaltsanbieter          | QuickTime:Microsoft:Video:Content Distributor |
| Ursprung     | Medium erstellt          | Quicktime:Time:CreateDate                     |
| Ursprung     | Codiert durch            | QuickTime:Microsoft:Video:Encoded By          |
| Ursprung     | Autoren-URL              | QuickTime:Microsoft:Author:Author URL         |
| Ursprung     | Angebots-URL             | QuickTime:Microsoft:Video:Promotion URL       |
| Inhalte      | Jugendschutz             | QuickTime:Microsoft:Video:Parental Rating     |
| Inhalte      | Komponisten              | QuickTime:ItemList:Audio:Composer             |
| Inhalte      | Dirigenten               | QuickTime:Microsoft:Video:Conductor           |
| Inhalte      | Zeitraum                 | QuickTime:Microsoft:Video:Period              |
| Inhalte      | Stimmung                 | QuickTime:Microsoft:Video:Mood                |
| Inhalte      | Ursprünglicher Schlüssel | QuickTime:Microsoft:Video:Initial Key         |
| Inhalte      | Beats pro Minute         | QuickTime:ItemList:Audio:Beats Per Minute     |


## Zoner Photo Studio X

### Mapping to Sidecar file
Zoner X saves the metadata in an XMP sidecar file.
The mapping from ZPS X to the XMP sidecar file is as follows:

| Kategorie         | Field                        | Metadata Field                                    |
| ----------------- | ---------------------------- | ------------------------------------------------- |
| Textinformationen | Name                         | dc:title                                          |
| Textinformationen | Autor                        | dc:creator                                        |
| Textinformationen | Copyright                    | dc:rights                                         |
| Textinformationen | Beschreibung                 | dc:description                                    |
| Textinformationen | Beschreibung - Autor         | photoshop:CaptionWriter                           |
| Textinformationen | Farbmarkierung               | xmp:Label                                         |
| Textinformationen | Bewertung                    | xmp:Rating <br/> znr:Rating                       |
| Fotoinformationen | Erstellt                     | photoshop:DateCreated <br/> exif:DateTimeOriginal |
| Fotoinformationen | Digitalisiert                | xmp:CreateDate                                    |
| Fotoinformationen | Empfindlichkeit              | N/A                                               |
| Fotoinformationen | Belichtungszeit              | N/A                                               |
| Fotoinformationen | Blende                       | N/A                                               |
| Fotoinformationen | Brennweite                   | N/A                                               |
| Fotoinformationen | Brennweite (EQ35mm)          | N/A                                               |
| Fotoinformationen | Objektiv                     | exifEX:LensModel                                  |
| Fotoinformationen | Hersteller des Objektivs     | exifEX:LensMake                                   |
| Fotoinformationen | Hersteller der Kamera        | tiff:Make                                         |
| Fotoinformationen | Kameramodell                 | tiff:Model                                        |
| Fotoinformationen | Transformation               | N/A                                               |
| Fotoinformationen | Geographische Breite         | exif:GPSLatitude                                  |
| Fotoinformationen | Geographische Länge          | exif:GPSLongitude                                 |
| Fotoinformationen | Höhe über dem Meeresspiegel  | exif:GPSAltitude <br/> exif:GPSAltitudeRef        |
| Fotoinformationen | Digitale Unterschrift        | N/A                                               |
| Fotoinformationen | Dynamikumfang                | N/A                                               |
| Fotoinformationen | Primärfarben                 | N/A                                               |
| Fotoinformationen | Weisspunkt                   | N/A                                               |
| Fotoinformationen | Übertragungscharakteristik   | N/A                                               |
| Schlüsselwörter   | Gewählte Schlüsselwörter     | dc:subject                                        |
| Bildquellen       | Ort                          | Iptc4xmpCore:Location                             |
| Bildquellen       | Stadt                        | photoshop:City                                    |
| Bildquellen       | Land/Provinz                 | photoshop:State                                   |
| Bildquellen       | Land                         | photoshop:Country                                 |
| Bildquellen       | Ländercode                   | Iptc4xmpCore:CountryCode                          |
| Bildquellen       | Verdienste                   | photoshop:Credit                                  |
| Bildquellen       | Quelle                       | photoshop:Source                                  |
| Bildquellen       | Kopfzeile                    | photoshop:Headline                                |
| Bildquellen       | Anweisungen                  | photoshop:Instructions                            |
| Bildquellen       | Verweis zu Ursprung          | photoshop:TransmissionReference                   |
| Bildquellen       | Dringlichkeit                | photoshop:Urgency                                 |
| Benutzerinfo      | Name in Fremdsprache         | znr:InternationalTitle                            |
| Benutzerinfo      | Beschreibung in Fremdsprache | znr:InternationalDescription                      |
| Benutzerinfo      | Veröffentlicht in            | znr:PublishedIn                                   |
| Benutzerinfo      | Stativ                       | znr:tripod                                        |
| Benutzerinfo      | Filter                       | znr:filter                                        |
| Benutzerinfo      | Zwischenriing                | znr:mezikrouzek                                   |
| Benutzerinfo      | Film                         | znr:film                                          |
| Benutzerinfo      | Filmbeschriftung im Archiv   | znr:FilmArchiveLabel                              |
| Benutzerinfo      | Format                       | znr:FilmFormat                                    |
| Benutzerinfo      | Verwendung                   | znr:use                                           |


### Mapping from Windows Explorer
The mapping from the Windows Fileexplorer to the mp4 metadata available in ZPS X is as follows:

| Windows Category | Windows Field            | ZPS Category      | ZPS Field                |
| ---------------- | ------------------------ | ----------------- | ------------------------ |
| Beschreibung     | Titel                    | Textinformationen | Name                     |
| Beschreibung     | Untertitel               |                   |                          |
| Beschreibung     | Bewertung                | Textinformationen | Bewertung                |
| Beschreibung     | Markierung               | Schlüsselwörter   | Gewählte Schlüsselwörter |
| Beschreibung     | Kommentare               | Textinformationen | Kommentare               |
| Medien           | Mitwirkende Interpreten  | Textinformationen | Autor                    |
| Medien           | Jahr                     |                   |                          |
| Medien           | Genre                    |                   |                          |
| Ursprung         | Regisseure               |                   |                          |
| Ursprung         | Produzenten              |                   |                          |
| Ursprung         | Texter                   |                   |                          |
| Ursprung         | Herausgeber              |                   |                          |
| Ursprung         | Inhaltsanbieter          |                   |                          |
| Ursprung         | Medium erstellt          | Fotoinformationen | Erstellt                 |
| Ursprung         | Codiert durch            |                   |                          |
| Ursprung         | Autoren-URL              |                   |                          |
| Ursprung         | Angebots-URL             |                   |                          |
| Inhalte          | Jugendschutz             |                   |                          |
| Inhalte          | Komponisten              |                   |                          |
| Inhalte          | Dirigenten               |                   |                          |
| Inhalte          | Zeitraum                 |                   |                          |
| Inhalte          | Stimmung                 |                   |                          |
| Inhalte          | Ursprünglicher Schlüssel |                   |                          |
| Inhalte          | Beats pro Minute         |                   |                          |


## Exif-Tool
You can write the metadata from a sidecar file to an MP4 file as follows:
```
.\exiftool.exe -tagsfromfile XMP_FILE FILE
```

The mapping from the sidecar file to the file metadata is as follows:

| Sidecar Field                   | File XMP Metadata                              | File Quicktime Metadata |
| ------------------------------- | ---------------------------------------------- | ----------------------- |
| dc:title                        | XMP:XMP-dc:Image:Title                         | -                       |
| dc:creator                      | XMP:XMP-dc:Author:Creator                      | -                       |
| dc:rights                       | XMP:XMP-dc:Author:Rights                       | -                       |
| dc:description                  | XMP:XMP-dc:Image:Description                   | -                       |
| dc:subject                      | XMP:XMP-dc:Image:Subject                       | -                       |
| photoshop:CaptionWriter         | XMP:XMP-photoshop:Author:Caption Writer        | -                       |
| photoshop:DateCreated           | XMP:XMP-photoshop:Time:Date Created            | -                       |
| photoshop:City                  | XMP:XMP-photoshop:Location:City                | -                       |
| photoshop:State                 | XMP:XMP-photoshop:Location:State               | -                       |
| photoshop:Country               | XMP:XMP-photoshop:Location:Country             | -                       |
| photoshop:Credit                | XMP:XMP-photoshop:Author:Credit                | -                       |
| photoshop:Source                | XMP:XMP-photoshop:Author:Source                | -                       |
| photoshop:Headline              | XMP:XMP-photoshop:Image:Headline               | -                       |
| photoshop:Instructions          | XMP:XMP-photoshop:Image:Instructions           | -                       |
| photoshop:TransmissionReference | XMP:XMP-photoshop:Image:Transmission Reference | -                       |
| photoshop:Urgency               | XMP:XMP-photoshop:Image:Urgency                | -                       |
| xmp:Label                       | XMP:XMP-xmp:Image:Label                        | -                       |
| xmp:Rating                      | XMP:XMP-xmp:Image:Rating                       | -                       |
| xmp:CreateDate                  | XMP:XMP-xmp:Time:Create Date                   | -                       |
| znr:Rating                      | -                                              | -                       |
| znr:InternationalTitle          | -                                              | -                       |
| znr:InternationalDescription    | -                                              | -                       |
| znr:PublishedIn                 | -                                              | -                       |
| znr:tripod                      | -                                              | -                       |
| znr:filter                      | -                                              | -                       |
| znr:mezikrouzek                 | -                                              | -                       |
| znr:film                        | -                                              | -                       |
| znr:FilmArchiveLabel            | -                                              | -                       |
| znr:FilmFormat                  | -                                              | -                       |
| znr:use                         | -                                              | -                       |
| exif:DateTimeOriginal           | XMP:XMP-exif:Time:Date/Time Original           | -                       |
| exif:GPSLongitude               | XMP:XMP-exif:Location:GPS Longitude            | -                       |
| exif:GPSLatitude                | XMP:XMP-exif:Location:GPS Latitude             | -                       |
| exif:GPSAltitude                | XMP:XMP-exif:Location:GPS Altitude             | -                       |
| exif:GPSAltitudeRef             | XMP:XMP-exif:Location:GPS Altitude Ref         | -                       |
| tiff:Make                       | XMP:XMP-tiff:Camera:Make                       | -                       |
| tiff:Model                      | XMP:XMP-tiff:Camera:Camera Model Name          | -                       |
| exifEX:LensModel                | XMP:XMP-exifEX:Camera:Lens Model               | -                       |
| exifEX:LensMake                 | XMP:XMP-exifEX:Camera:Lens Make                | -                       |
| Iptc4xmpCore:CountryCode        | XMP:XMP-iptcCore:Location:Country Code         | -                       |
| Iptc4xmpCore:Location           | XMP:XMP-iptcCore:Location:Location             | -                       |


## Synology Photos

### Information
The mapping from the JPEG metadata to the Syonology Photos metadata in the tab Information is as follows (see also [this article](https://kb.synology.com/en-uk/DSM/tutorial/What_metadata_standards_does_Synology_Photos_support)):

| Synology Photos Field | Metadata Field                                                                                                  |
| --------------------- | --------------------------------------------------------------------------------------------------------------- |
| Description           | N/A                                                                                                             |
| Rating                | N/A                                                                                                             |
| Date                  | 1. QuickTime:Keys:Time:CreationDate <br/> 2. QuickTime:Time:CreateDate <br/> 3. File:System:Time:FileModifyDate |
| Tags                  | N/A                                                                                                             |

### More
The mapping from the MP4 v2 metadata to the Syonology Photos metadata in the tab More is as follows:

| Synology Photos Field            | Metadata Field                               | check |
| -------------------------------- | -------------------------------------------- | ----- |
| Audio Channel Type               | QuickTime:Track2:Audio:Audio Channels        | x     |
| Audio Compressor                 | QuickTime:Track2:Audio:Audio Format          | x     |
| Audio Sample Rate                | QuickTime:Track2:Audio:Audio Sample Rate     | x     |
| Audio Track Create Date          | QuickTime:Track1:Time:Track Create Date      | x     |
| Audio Track Duration             | QuickTime:Track1:Video:Track Duration        | todo  |
| Audio Track Layer                | QuickTime:Track1:Video:Track Layer           | todo  |
| Audio Track Modify Date          | QuickTime:Track1:Time:Track Modify Date      | x     |
| Balance                          | QuickTime:Track2:Audio:Balance               | x     |
| Bit Depth                        | QuickTime:Track1:Image:Bit Depth             | x     |
| Bits Per Sample / Bit Rate       | QuickTime:Track2:Audio:Audio Bits Per Sample | x     |
| Current Time                     | QuickTime:Video:Current Time                 | x     |
| Date-Time Original               | 1. QuickTime:Time:CreateDate <br/> 2. ?      | todo  |
| Duration                         | QuickTime:Video:Duration                     | x     |
| File Name                        | File:System:Other:File Name                  | x     |
| File Size                        | File:System:Other:File Size                  | x     |
| Graphics Mode                    | QuickTime:Track1:Video:Graphics Mode         | x     |
| Handler Type                     | QuickTime:Track2:Video:Handler Type          | todo  |
| Media Header Version             | QuickTime:Track2:Video:Media Header Version  | x     |
| Media Language Code              |                                              | todo  |
| Media Time Scale                 |                                              | todo  |
| Media Track Create Date          | QuickTime:Track2:Time:Media Create Date      | x     |
| Media Track Duration             | QuickTime:Track2:Video:Media Duration        | x     |
| Media Track Modify Date          | QuickTime:Track2:Time:Media Modify Date      | x     |
| Mime Type                        | File:Other:MIME Type                         | x     |
| Modification Date-Time           | QuickTime:Time:Modify Date                   | x     |
| Movie Header Version             | QuickTime:Video:Movie Header Version         | x     |
| Next Track ID                    | QuickTime:Video:Next Track ID                | x     |
| Operation Colours                | QuickTime:Track1:Video:Op Color              | x     |
| Play Mode                        | QuickTime:UserData:Video:Play Mode           | x     |
| Poster Time                      | QuickTime:Video:Poster Time                  | x     |
| Preferred Rate                   | QuickTime:Video:Preferred Rate               | x     |
| Preferred Volume                 | QuickTime:Video:Preferred Volume             | x     |
| Preview Duration                 | QuickTime:Video:Preview Duration             | x     |
| Preview Time                     | QuickTime:Video:Preview Time                 | x     |
| QTime Compatible FileType Brand  | QuickTime:Video:Compatible Brands            | x     |
| QTime Major FileType Brand       | QuickTime:Video:Major Brand                  | x     |
| QTime Minor FileType Version     | QuickTime:Video:Minor Version                | x     |
| Selection Duration               | QuickTime:Video:Selection Duration           | x     |
| Selection Time                   | QuickTime:Video:Selection Time               | x     |
| Source Image Height              | QuickTime:Track1:Image:Source Image Height   | x     |
| Source Image Width               | QuickTime:Track1:Image:Source Image Width    | x     |
| Time Scale                       | QuickTime:Video:Time Scale                   | x     |
| Track Header Version             | QuickTime:Track1:Video:Track Header Version  | x     |
| Track ID                         | QuickTime:Track1:Video:Track ID              | x     |
| Track Volume                     | QuickTime:Track1:Video:Track Volume          | x     |
| Video Aspect Ratio               |                                              | todo  |
| Video Codec                      |                                              | todo  |
| Video Frame Rate                 | QuickTime:Track1:Video:Video Frame Rate      | x     |
| Video Height                     | QuickTime:Track1:Video:Image Height          | x     |
| Video Track Create Date          | QuickTime:Track1:Time:Track Create Date      | x     |
| Video Track Duration             |                                              | todo  |
| Video Track Layer                |                                              | todo  |
| Video Track Modify Date          | QuickTime:Track1:Time:Track Modify Date      | x     |
| Video Width                      | QuickTime:Track1:Video:Image Width           | x     |
| X Resolution                     | QuickTime:Track1:Image:X Resolution          | x     |
| Y Resolution                     | QuickTime:Track1:Image:Y Resolution          | x     |
| com.android.capture.fps          | QuickTime:Keys:Other:Android Capture FPS     | x     |
| com.android.version              | QuickTime:Keys:Other:Android Version         | x     |
| com.apple.quicktime.creationdate | QuickTime:Keys:Time:CreationDate             | x     |



### Set Creation Date
TODO
I don't know why, but MP4 files haven't set the information when just upload it to synology Photos.
To set all metadata correctly, just reset the CreateDate of the file:
```
.\exiftool.exe -QuickTime:Keys:Time:CreationDate<QuickTime:Time:CreateDate FILE
.\exiftool.exe -QuickTime:Keys:Time:CreationDate>QuickTime:Time:CreateDate FILE
```


### Set GPS

Unfortunately, Synology Photos is not able to read GPS information from MP4 files.
Anyway - I like to write GPS information directly into the metadata of the file, as it was read before by photostation into the following fields:
- XMP:XMP-exif:Location:GPSLatitude
- XMP:XMP-exif:Location:GPSLongitude
- XMP:XMP-exif:Location:GPSAltitude
- XMP:XMP-exif:Location:GPSAltitudeRef

You can write data from a sidecar file (XMP_FILE) to the metadata of a mp4 file (FILE) with the following command:
```
.\exiftool.exe -tagsfromfile XMP_FILE FILE
```
You can use format options to read the file where:
- %f = filename
- %d = directory
- %e = extension
- 
For example if the sidecar file has the same name as the mp4 file and it is in the same folder, use: 
```
.\exiftool.exe -tagsfromfile %f.xmp FILE
```

Then make sure that the GPS information is also stored in the metadata field `QuickTime:UserData:Location:GPSCoordinates`:
```
.\exiftool.exe -Composite:GPSPosition>QuickTime:UserData:Location:GPSCoordinates FILE
```

### All in One
For each folder containing MP4 with the corresponding XMP files, execute:
```
# Set Creation Date
.\exiftool.exe -ext mp4 -overwrite_original -QuickTime:Keys:Time:CreationDate<QuickTime:Time:CreateDate .
.\exiftool.exe -ext mp4 -overwrite_original -QuickTime:Keys:Time:CreationDate>QuickTime:Time:CreateDate .
.\exiftool.exe -ext mp4 -overwrite_original -QuickTime:Keys:Time:CreationDate= .

# Set GPS
.\exiftool.exe -ext mp4 -overwrite_original -tagsfromfile %f.xmp .
.\exiftool.exe -ext mp4 -overwrite_original -Composite:GPSPosition>QuickTime:UserData:Location:GPSCoordinates .
```

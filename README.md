# MP4 Metadata Management
Manage mp4 Metadata for quicktime videos

I use Zoner Photo Studio X to manage my video metadata.
It was timeconsuming to find out which metadata is used by different programs. The most painful metadata fields are GPS and CreateDate.
With this document I would like to create some clarity.

To manage the metadata, I use the following tools:
- [ffmpeg](https://ffmpeg.org/)
- [ExifTool](https://exiftool.org/)

**Table of Content**
- [MP4 Metadata Management](#mp4-metadata-management)
  - [ExifTool](#exiftool)
  - [ffmpeg](#ffmpeg)
  - [Zoner Photo Studio X](#zoner-photo-studio-x)
  - [Synology Photos](#synology-photos)
    - [Metadata  Mapping](#metadata--mapping)
    - [Creation Date](#creation-date)
    - [GPS](#gps)
    - [All in One](#all-in-one)
    - [File Format](#file-format)
  - [OneDrive Photos](#onedrive-photos)
    - [Creation Date](#creation-date-1)
    - [GPS](#gps-1)


## ExifTool
ExifTool is a great tool to work with metadata.
Use the parameter `-overwrite_original` to write directly to the file and not to create a backup copy.

Here some useful commands:

```
# List all metadata and do not generate composite tags
.\exiftool.exe -a -e FILE

# List all Time related metadata
.\exiftool.exe -a -e -G0:1:2 -Time:all FILE

# List all GPS related metadata
.\exiftool.exe -a -e -G0:1:2 -*GPS* FILE

# Exclude Track1 family
.\exiftool.exe -a -e -G0:1:2 --Track1:all FILE


# Write tags from an XMP sidecar file to the metadata of the mp4 file
.\exiftool.exe -tagsfromfile %f.xmp 'FILE'

```

The mapping from the Sidecar File to the Metadata is as follows:

| Sidecar Field                   | XMP Metadata                                    | Quicktime Metadata                         |
| ------------------------------- | ----------------------------------------------- | ------------------------------------------ |
| dc:title                        | XMP:XMP-dc:Image:Title                          | QuickTime:ItemList:Audio:Title             |
| dc:creator                      | XMP:XMP-dc:Author:Creator                       | -                                          |
| dc:rights                       | XMP:XMP-dc:Author:Rights                        | -                                          |
| dc:description                  | XMP:XMP-dc:Image:Description                    | QuickTime:ItemList:Audio:Description       |
| photoshop:CaptionWriter         | XMP:XMP-photoshop:Author:Caption Writer         | -                                          |
| xmp:Rating                      | XMP:XMP-xmp:Image:Rating                        | -                                          |
| znr:Rating                      | -                                               | -                                          |
| exif:DateTimeOriginal           | XMP:XMP-exif:Time:Date/Time Original            | QuickTime:UserData:Time:Date/Time Original |
| photoshop:DateCreated           | XMP:XMP-photoshop:Time:Date Created             | -                                          |
| xmp:CreateDate                  | XMP:XMP-xmp:Time:Create Date                    | QuickTime:Time:Create Date                 |
| exif:ExposureTime               | XMP:XMP-exif:Image:Exposure Time                | -                                          |
| exif:FNumber                    | XMP:XMP-exif:Image:F Number                     | -                                          |
| exif:FocalLength                | XMP:XMP-exif:Camera:Focal Length                | -                                          |
| exif:FocalLengthIn35mmFilm      | XMP:XMP-exif:Camera:Focal Length In 35mm Format | -                                          |
| exifEX:LensModel                | XMP:XMP-exifEX:Camera:Lens Model                | -                                          |
| exifEX:LensMake                 | XMP:XMP-exifEX:Camera:Lens Make                 | -                                          |
| tiff:Make                       | XMP:XMP-tiff:Camera:Make                        | QuickTime:UserData:Video:Make              |
| tiff:Model                      | XMP:XMP-tiff:Camera:Camera Model Name           | QuickTime:UserData:Video:Model             |
| dc:subject                      | XMP:XMP-dc:Image:Subject                        | -                                          |
| Iptc4xmpCore:Location           | XMP:XMP-iptcCore:Location:Location              | -                                          |
| photoshop:City                  | XMP:XMP-photoshop:Location:City                 | -                                          |
| photoshop:State                 | XMP:XMP-photoshop:Location:State                | -                                          |
| photoshop:Country               | XMP:XMP-photoshop:Location:Country              | -                                          |
| Iptc4xmpCore:CountryCode        | XMP:XMP-iptcCore:Location:Country Code          | -                                          |
| photoshop:Credit                | XMP:XMP-photoshop:Author:Credit                 | -                                          |
| photoshop:Source                | XMP:XMP-photoshop:Author:Source                 | -                                          |
| photoshop:Headline              | XMP:XMP-photoshop:Image:Headline                | -                                          |
| photoshop:Instructions          | XMP:XMP-photoshop:Image:Instructions            | -                                          |
| photoshop:TransmissionReference | XMP:XMP-photoshop:Image:Transmission Reference  | -                                          |
| photoshop:Urgency               | XMP:XMP-photoshop:Image:Urgency                 | -                                          |
| znr:InternationalTitle          | -                                               | -                                          |
| znr:InternationalDescription    | -                                               | -                                          |
| znr:PublishedIn                 | -                                               | -                                          |
| znr:tripod                      | -                                               | -                                          |
| znr:filter                      | -                                               | -                                          |
| znr:mezikrouzek                 | -                                               | -                                          |
| znr:film                        | -                                               | -                                          |
| znr:FilmArchiveLabel            | -                                               | -                                          |
| znr:FilmFormat                  | -                                               | -                                          |
| znr:use                         | -                                               | -                                          |
| exif:GPSLatitude                | XMP:XMP-exif:Location:GPS Latitude              | -                                          |
| exif:GPSLongitude               | XMP:XMP-exif:Location:GPS Longitude             | -                                          |
| exif:GPSAltitude                | XMP:XMP-exif:Location:GPS Altitude              | -                                          |
| exif:GPSAltitudeRef             | XMP:XMP-exif:Location:GPS Altitude Ref          | -                                          |


Some information to timestamp format:
| Metadata                                   | Format                    |
| ------------------------------------------ | ------------------------- |
| QuickTime:UserData:Time:Date/Time Original | 9999:99:99 99:99:99+99:99 |
| XMP:XMP-exif:Time:Date/Time Original       | 9999:99:99 99:99:99       |
| XMP:XMP-photoshop:Time:Date Created        | 9999:99:99 99:99:99       |
| QuickTime:Time:Create Date                 | 9999:99:99 99:99:99       |
| XMP:XMP-xmp:Time:Create Date               | 9999:99:99 99:99:99.999   |


## ffmpeg
ffmpeg is a great tool to convert videos from one format into the other.

Here some useful commands:

```
# convert .mov video file with H264 encoding:
.\ffmpeg.exe  -i .\input.mov -c:v libx264 -c:a copy .\output.mp4

```


## Windows File Explorer
The mapping from the Windows Fileexplorer to the mp4 metadata is as follows:

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
The mapping from the Windows Fileexplorer to the mp4 metadata available in ZPS X is as follows:

| Kategorie         | Field                        | Sidecar Field                                      |
| ----------------- | ---------------------------- | -------------------------------------------------- |
| Textinformationen | Name                         | dc:title                                           |
| Textinformationen | Autor                        | dc:creator                                         |
| Textinformationen | Copyright                    | dc:rights                                          |
| Textinformationen | Beschreibung                 | dc:description                                     |
| Textinformationen | Beschreibung - Autor         | photoshop:CaptionWriter                            |
| Textinformationen | Bewertung                    | xmp:Rating <br/> znr:Rating                        |
| Fotoinformationen | Erstellt                     | exif:DateTimeOriginal <br/ > photoshop:DateCreated |
| Fotoinformationen | Digitalisiert                | xmp:CreateDate                                     |
| Fotoinformationen | Empfindlichkeit              |                                                    |
| Fotoinformationen | Belichtungszeit              | exif:ExposureTime                                  |
| Fotoinformationen | Blende                       | exif:FNumber                                       |
| Fotoinformationen | Brennweite                   | exif:FocalLength                                   |
| Fotoinformationen | Brennweite (EQ35mm)          | exif:FocalLengthIn35mmFilm                         |
| Fotoinformationen | Objektiv                     | exifEX:LensModel                                   |
| Fotoinformationen | Hersteller des Objektivs     | exifEX:LensMake                                    |
| Fotoinformationen | Hersteller der Kamera        | tiff:Make                                          |
| Fotoinformationen | Transformation               | tiff:Model                                         |
| Schlüsselwörter   | Gewählte Schlüsselwörter     | dc:subject                                         |
| Bildquellen       | Ort                          | Iptc4xmpCore:Location                              |
| Bildquellen       | Stadt                        | photoshop:City                                     |
| Bildquellen       | Land/Provinz                 | photoshop:State                                    |
| Bildquellen       | Land                         | photoshop:Country                                  |
| Bildquellen       | Ländercode                   | Iptc4xmpCore:CountryCode                           |
| Bildquellen       | Verdienste                   | photoshop:Credit                                   |
| Bildquellen       | Quelle                       | photoshop:Source                                   |
| Bildquellen       | Kopfzeile                    | photoshop:Headline                                 |
| Bildquellen       | Anweisungen                  | photoshop:Instructions                             |
| Bildquellen       | Verwies zu Ursprung          | photoshop:TransmissionReference                    |
| Bildquellen       | Dringlichkeit                | photoshop:Urgency                                  |
| Benutzerinfo      | Name in Fremdsprache         | znr:InternationalTitle                             |
| Benutzerinfo      | Beschreibung in Fremdsprache | znr:InternationalDescription                       |
| Benutzerinfo      | Veröffentlicht in            | znr:PublishedIn                                    |
| Benutzerinfo      | Stativ                       | znr:tripod                                         |
| Benutzerinfo      | Filter                       | znr:filter                                         |
| Benutzerinfo      | Zwischenring                 | znr:mezikrouzek                                    |
| Benutzerinfo      | Film                         | znr:film                                           |
| Benutzerinfo      | Filmbeschriftung im Archiv   | znr:FilmArchiveLabel                               |
| Benutzerinfo      | Format                       | znr:FilmFormat                                     |
| Benutzerinfo      | Verwendung                   | znr:use                                            |
| GPS               | Geographische Breite         | exif:GPSLatitude                                   |
| GPS               | Geographische Länge          | exif:GPSLongitude                                  |
| GPS               | Höhe über dem Meer           | exif:GPSAltitude                                   |
| GPS               |                              | exif:GPSAltitudeRef                                |


## Synology Photos

### Metadata  Mapping

| Metadata field                           | Synology Photos                  |
| ---------------------------------------- | -------------------------------- |
| QuickTime:Keys:Time:CreationDate         | com.apple.quicktime.creationdate |
| QuickTime:Time:ModifyDate                | Modification Date-Time           |
| QuickTime:Track1:Time:TrackCreateDate    | Video Track Create Date          |
| QuickTime:Track1:Time:TrackModifyDate    | Video Track Modify Date          |
| QuickTime:Track1:Time:MediaCreateDate    | Media Track Create Date          |
| QuickTime:Track1:Time:MediaModifyDate    | Media Track Modify Date          |
| QuickTime:Track2:Time:TrackCreateDate    | Audio Track Create Date          |
| QuickTime:Track2:Time:TrackModifyDate    | Audio Track Modify Date          |
| QuickTime:UserData:Time:DateTimeOriginal | -                                |
| QuickTime:Time:CreateDate                | Date-Time Original               |


### Creation Date

The Creation Date can be read from different fields as mentioned in the table below.
See also this [article](https://kb.synology.com/en-global/DSM/tutorial/What_can_I_do_if_Synology_Photos_shows_incorrect_dates_of_my_photos)

| Metadata field                   | Synology Photos                  | Prio |
| -------------------------------- | -------------------------------- | ---- |
| QuickTime:Keys:Time:CreationDate | com.apple.quicktime.creationdate | 1    |
| QuickTime:Time:CreateDate        | Date-Time Original               | 2    |
| File:System:Time:FileModifyDate  | ?                                | 3    |

I don't know why, but MP4 files haven't set the information when just upload it to synology Photos.
To set all metadata correctly, just reset the CreateDate of the file:
```
.\exiftool.exe -QuickTime:Keys:Time:CreationDate<QuickTime:Time:CreateDate FILE
.\exiftool.exe -QuickTime:Keys:Time:CreationDate>QuickTime:Time:CreateDate FILE
.\exiftool.exe -QuickTime:Keys:Time:CreationDate= FILE
```

I don't set CreationDate because of timezone problems. See [this post](https://community.synology.com/enu/forum/1/post/138615).


### GPS

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

### File Format

Synology photos doesn't preview .mov videos. Therfore I convert them with ffmpeg to .mp4 files using the following command:

```
ffmpeg -i INPUT.mov \
  -c:v libx264 \
  -crf 17 \
  -c:a copy \
  -brand mp42:0
  OUTPUT.mp4
```

- **-c:v libx264**: convert the video file with H264 encoding
- **-crf 17 crf**: Constant Rate Factor
- **-c:a copy**: Copy the audio from original video to destination video file
- **-brand mp42:0**: Use Major Brand "MP4 v2 [ISO 14496-14]"

## OneDrive Photos

### Creation Date

OneDrive Photos is not able to read the Creation Date of MP4 v2 files (or at least I didn't figure out how to do it). It can only read it from MP4 Base Media v1 files.

To convert an MP4 file from v2 to v1, execute:
```
.\ffmpeg.exe -i INPUT -vcodec copy -acodec copy OUTPUT
```

This will remove all media related metadata. After that, set the creation date as follows:
```
.\exiftool.exe -XMP:XMP-xmp:Time:CreateDate="2005:09:22 13:24:22" FILE
```

### GPS
OneDrive Photos is not able to read GPS data containing
- Altitude
- AltitudeRef
- LongitudeRef
- LatitudeRef

To add the GPS from the XMP file of Zoner, execute the following:
```
.\exiftool.exe FILE -LocationInformation=
.\exiftool.exe FILE -tagsfromfile XMP_FILE
.\exiftool.exe FILE -UserData:GPSCoordinates<Composite:GPSPosition
.\exiftool.exe FILE -XMP-exif:all=
```

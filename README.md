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
  - [Zoner Photo Studio X](#zoner-photo-studio-x)
  - [Synology Photos](#synology-photos)
    - [Mapping](#mapping)
    - [Creation Date](#creation-date)
    - [GPS](#gps)
    - [All in One](#all-in-one)
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

```

## Zoner Photo Studio X
The mapping from the Windows Fileexplorer to the mp4 metadata available in ZPS X is as follows:

| Windows File Explorer   | ZPS X           | Metadata Field                     |
| ----------------------- | --------------- | ---------------------------------- |
| Titel                   | Titel           | QuickTime:ItemList:Audio:Title     |
| Kommentare              | Beschreibung    | QuickTime:ItemList:Audio:Comment   |
| Markierung              | Schlüsselwörter | QuickTime:Microsoft:Video:Category |
| Mitwirkende Interpreten | Autor           | QuickTime:ItemList:Audio:Artist    |
| Medium erstellt         | Erstellt        | Quicktime:Time:CreateDate          |

ZPS X writes GPS information to a sidecar file.
Unfortunately, Synology Photos is not able to read GPS information from mp4 files.
I like to write this information directly into the following file metadata:

| ZPS X                | Sidecar field       |
| -------------------- | ------------------- |
| Geographische Breite | exif:GPSLatitude    |
| Geographische Länge  | exif:GPSLongitude   |
| Höhe über dem Meer   | exif:GPSAltitude    |
|                      | exif:GPSAltitudeRef |


## Synology Photos

### Mapping

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
To set all metadata correctly, just update the creation date of the file:
```
.\exiftool.exe -QuickTime:Keys:Time:CreationDate<QuickTime:Time:CreateDate FILE
```

### GPS

Unfortunately, Synology Photos is not able to read GPS information from MP4 files.
Anyway - I like to write GPS information directly into the metadata of the file, as it was read before by photostation:

| ZPS X                | Sidecar field       | Metadata Field                       |
| -------------------- | ------------------- | ------------------------------------ |
| Geographische Breite | exif:GPSLatitude    | XMP:XMP-exif:Location:GPSLatitude    |
| Geographische Länge  | exif:GPSLongitude   | XMP:XMP-exif:Location:GPSLongitude   |
| Höhe über dem Meer   | exif:GPSAltitude    | XMP:XMP-exif:Location:GPSAltitude    |
| Höhe über dem Meer   | exif:GPSAltitudeRef | XMP:XMP-exif:Location:GPSAltitudeRef |

You can write data from an XMP_FILE to the metadata of a FILE with the following command:
```
.\exiftool.exe -tagsfromfile XMP_FILE FILE
```
You can use format options to read the file where:
- %f = filename
- %d = directory
- %e = extension
For example if the XMP_FILE has the same name as the FILE and is in the same folder, use: 
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
.\exiftool.exe -ext mp4 -QuickTime:Keys:Time:CreationDate<QuickTime:Time:CreateDate .

# Set GPS
.\exiftool.exe -ext mp4 -tagsfromfile %f.xmp .
.\exiftool.exe -ext mp4 -Composite:GPSPosition>QuickTime:UserData:Location:GPSCoordinates .
```


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

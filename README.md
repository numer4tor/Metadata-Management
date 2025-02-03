# Metadata Management

I use Zoner Photo Studio X to manage my video metadata.
It was timeconsuming to find out which metadata is used by different programs. The most painful metadata fields are GPS and CreateDate.
With this project I would like to create some clarity.

The metadata mapping can be found in the corresponding markdown files:
- [JPEG](./JPEG.md)
- [MP4v1](./MP4v1.md)
- [MP4v2](./MP4v2.md)

To manage the metadata, I use the following tools:
- [ExifTool](https://exiftool.org/)
- [ffmpeg](https://ffmpeg.org/)


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

# Only select lines containing TEXT
.\exiftool.exe -a -e FILE | select-string -pattern TEXT

# Write tags from an XMP sidecar file to the metadata of the MP4 file with the same name
# %f = filename
# %d = directory
# %e = extension
.\exiftool.exe -tagsfromfile %f.xmp 'FILE'

# Do the same as the last command but for all files in a folder ending with .mp4
.\exiftool.exe -ext mp4 -overwrite_original -tagsfromfile %f.xmp .

# Set all dates
.\exiftool.exe -AllDates="2023-07-08 16:00:00" . -overwrite_original

# Set all dates increased by 30 seconds ordered by filename for all files in the current folder
.\exiftool.exe '-AllDates+<00:00:${filesequence;$_*=30}' . -fileorder filename -overwrite_original

```


## ffmpeg
ffmpeg is a great tool to convert videos from one format into the other.

Here some useful commands:

```
# convert .mov video file with H264 encoding:
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



## How to organize files

To organize my files, I do the following:
1. Set Metadata in Zoner Photo Studio X
2. Add metadata to files according to XMP files
3. Remove UserComment
4. Add additional metadata not available in Zoner Photo Studio X
5. Rename Files


### Set Metadata in Zoner Photo Studio X

I use the following Tags:
- Arbeit
- Biken
- Bushness
- Familie
- Ferien
- Geburtstag
- Geocaching
- Gymer
- Hochzeit
- Konzert
- Landschaft
- Laufen
- Motorrad
- Openair
- Pubquiz
- Paradise Kid
- Schule
- Skifahren
- Studium
- UHC WWSB
- Wandern


### Add metadata to files according to XMP files

This can be done with the following commands:
```
# Set metadata according to XMP file
.\exiftool.exe -ext mp4 -ext mov -ext gif -overwrite_original -tagsfromfile %f.xmp .
```

### Remove UserComment

Zoner Photo Studio X sets the metadata field UserComment for JPEG files, which cannot be read by Synology Photos. Therefore I remove it.

```
# Remove UserComment
.\exiftool.exe -ext jpg -ext jpeg -ext png -overwrite_original -EXIF:ExifIFD:Image:UserComment= .
```


### Add additional metadata not available in Zoner Photo Studio X

I add the following additional metadata:
- JPEG & MP4: Offset Time
- MP4: GPS

```
# Set Offset Time for images
.\exiftool.exe -ext jpg -ext jpeg -ext png -overwrite_original -EXIF:ExifIFD:Time:OffsetTime="+02:00" .
.\exiftool.exe -ext jpg -ext jpeg -ext png -overwrite_original -EXIF:ExifIFD:Time:OffsetTimeOriginal="+02:00" .

# Only if necessary - set all dates for movies
.\exiftool.exe -ext mp4 -ext mov -ext gif -overwrite_original -AllDates<xmp:xmp-exif:time:datetimeoriginal .

# Set CreationDate for movies
.\exiftool.exe -ext mp4 -ext mov -ext gif -overwrite_original '-QuickTime:Keys:Time:CreationDate<${QuickTime:Time:CreateDate}+02:00' .

# Set GPS
.\exiftool.exe -ext mp4 -ext mov -ext gif -overwrite_original -Composite:GPSPosition>QuickTime:UserData:Location:GPSCoordinates .
```

### Rename Files

I rename files according to the creation date. I do this in Zoner Photo Studio X by using the function "Stapelverarbeitung - Umbenennen" with the following input:
- Dateiname: {Y}{M}{D}\_{h}{m}{s}\_{C}
- Dateierweiterung: {E}
- Datumstyp: Erstellungsdatum
- Beginn bei: 1
- Erhöhen um: 1
- Ziffern: 3

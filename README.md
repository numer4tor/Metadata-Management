# Metadata Management

I use Zoner Photo Studio X to manage my video metadata.
It was timeconsuming to find out which metadata is used by different programs. The most painful metadata fields are GPS and CreateDate.
With this project I would like to create some clarity.

The metadata mapping can be found in the corresponding markdown files:
- [JPEG](./JPEG.md)
- [MP4](./MP4.md)

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

# Write tags from an XMP sidecar file to the metadata of the mp4 file
.\exiftool.exe -tagsfromfile %f.xmp 'FILE'

```


## ffmpeg
ffmpeg is a great tool to convert videos from one format into the other.

Here some useful commands:

```
# convert .mov video file with H264 encoding:
.\ffmpeg.exe  -i .\input.mov -c:v libx264 -c:a copy .\output.mp4

```

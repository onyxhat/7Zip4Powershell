7Zip4Powershell
===============

Powershell module for creating and extracting 7-Zip archives supporting Powershell's WriteProgress API.

The syntax is simple as this:

    Expand-7Zip
        [-ArchiveFileName] <string>
        [-TargetPath] <string>
        [-Force]
        [<CommonParameters>]

    Compress-7Zip
        [-ArchiveFileName] <string>
        [-Path] <string>
        [[-Filter] <string>]
        [-Format <OutArchiveFormat> {SevenZip | Zip | GZip | BZip2 | Tar | XZ}]
        [-CompressionLevel <CompressionLevel> {None | Fast | Low | Normal | High | Ultra}]
        [-CompressionMethod <CompressionMethod> {Copy | Deflate | Deflate64 | BZip2 | Lzma | Lzma2 | Ppmd | Default}]
        [<CommonParameters>]

![Compress](https://github.com/onyxhat/7Zip4Powershell/blob/master/screenshots/Compress_Progress_1.png)
![UnCompress](https://github.com/onyxhat/7Zip4Powershell/blob/master/screenshots/UnCompress_Progress_1.png)
![UnCompress Force](https://github.com/onyxhat/7Zip4Powershell/blob/master/screenshots/UnCompress_Progress_2.png)
		
It works with both x86 and x64 and uses [SevenZipSharp](https://sevenzipsharp.codeplex.com/) as a wrapper around 7zip’s API.
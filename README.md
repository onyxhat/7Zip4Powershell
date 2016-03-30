# 7Zip4Powershell

Powershell module for creating and extracting 7-Zip archives supporting Powershell's `WriteProgress` API.

![Screenshot](https://github.com/onyxhat/7Zip4Powershell/blob/master/Assets/compression.gif)

## Usage

The syntax is simple as this:

```powershell
Expand-7Zip
    [-ArchiveFileName] <string> 
    [-TargetPath] <string>  
    [-Force] <switch>  
    [-Password] <string> 
    [-CustomInitialization <ScriptBlock>]
    [<CommonParameters>]
 
Compress-7Zip
    [-ArchiveFileName] <string> 
    [-Path] <string> 
    [[-Filter] <string>] 
    [-Password] <string> 
    [-Format <OutArchiveFormat> {SevenZip | Zip | GZip | BZip2 | Tar | XZ}] 
    [-CompressionLevel <CompressionLevel> {None | Fast | Low | Normal | High | Ultra}] 
    [-CompressionMethod <CompressionMethod> {Copy | Deflate | Deflate64 | BZip2 | Lzma | Lzma2 | Ppmd | Default}] 
    [-CustomInitialization <ScriptBlock>]
    [<CommonParameters>]
```

It works with both x86 and x64 and uses [SevenZipSharp](https://sevenzipsharp.codeplex.com/) as a wrapper around 7zip’s API.


## Customization

Both `Compress-7Zip` and `Expand-7Zip` accept script blocks for customization. The script blocks get passed the current
`SevenZipCompressor` and `SevenZipExtractor` instance respectively. E.g. you can set the multithread mode this way:

```powershell
$initScript = {
    param ($compressor)
    $compressor.CustomParameters.Add("mt", "off")
}

Compress-7Zip -Path . -ArchiveFileName demo.7z -CustomInitialization $initScript
```

A list of all custom parameters can be found [here](https://sevenzip.osdn.jp/chm/cmdline/switches/method.htm).

# mrxs2tiff

### 1. Application area
For digital pathology slides

### 2. Description 
A simple bash script to convert scanned digital whole slide images in the MIRAX _.mrxs_ format from 3DHistech to pyramidal _tiffs_ using the [vips](https://github.com/libvips/libvips) image processing library

### 3. Requires
- libvips
- OpenSlide & bigtiff

##### installation:
``` bash
sudo apt install libvips-dev 
sudo apt install openslide
```
NOTE: You can install openslide manually from [official site](https://openslide.org/download/)

### 4. Usage

##### clone and prepare _mrxs2tiff_ project:
```bash
git clone https://github.com/Survial53/mrxs2tiff.git
cd mrxs2tiff
chmod +x mrxs2tiff.sh
```

##### run with default params:

```bash
./mrxs2tiff.sh /path/to/your/file.mrxs/or/directory/
Converting 2341.mrxs with jpeg compression at 85 to 2341.tiff
vips temp-4: 116128 x 318328 pixels, 16 threads, 128 x 128 tiles, 384 lines in buffer
vips temp-4: done in 210s
```

##### params description:
```bash
./mrxs2tiff.sh --help
Usage: mrxs2tiff.sh [-h] [-v] [-Q] [-l] [-o] file1 [file2...]

Script to convert mrxs (MIRAX) files used by 3DHistech scanners to pyramidal tiffs with vips
Requires libvips, OpenSlide & bigtiff

Available options:

-h, --help      Print this help and exit
-v, --verbose   Print script debug info
-Q, --quality   Jpeg compression quality, defaults to 85
-l, --level     Slide level to convert, defaults to 0
-o, outputdir   defaults to .
--> arguments   list of .mrxs files to convert, defaults to all mrxs in path if none provided
```

### 5. OPTIONAL 
You can specify arguments for <b>_vips_</b> such as _tile size_ directly in script 

Also you can use <b>_vips_</b> directly:
```bash
vips tiffsave $INPUT[autocrop=true] $OUTPUT --tile --tile-width 256 --tile-height 256 --pyramid --bigtiff --compression=jpeg --Q 85 --vips-progress
```

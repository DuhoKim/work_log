## work_log

### Installing SExtractor on Mac (macOS 11.4 Big Sur)

Followed [this link](https://sextractor.readthedocs.io/en/latest/Installing.html) with [icc & MKL](https://software.intel.com/content/www/us/en/develop/articles/free-intel-software-developer-tools.html) option.

### Running SExtractor inside IDL interpreter

Had to symlink dynamically linked library files
```
sudo ln -s /path/original/libmkl_intel_lp64.1.dylib <@rpath>/libmkl_intel_lp64.1.dylib
sudo ln -s /path/original/libmkl_intel_thread.1.dylib <@rpath>/libmkl_intel_thread.1.dylib
sudo ln -s /path/original/libmkl_core.1.dylib <@rpath>/libmkl_core.1.dylib    
```
, where 

```
$rpath = /opt/intel/oneapi/compiler/2021.2.0/mac/compiler/lib # found by `otool -l /usr/local/bin/sex`
/path/original/ = /opt/intel/oneapi/mkl/2021.2.0/lib/ # found by `find / -name 'libmkl_intel_lp64.1.dylib' 2>/dev/null`
```
in my case, because setting up *Intel* environment by sourcing `/opt/intel/oneapi/setvars.sh` was not extended to the IDL intereter's environment I guess.


### Running GALAPAGOS2

Followed [this link](https://github.com/MegaMorph/galapagos/blob/master/EXAMPLE_AND_README/USAGE.md) 

#### Trouble shooting
1. Multi-extension Fits file was not supported. -> Splitted into single fits file using [splitfits.py](https://gist.github.com/vterron/24d904f4711006b07997) 
2. The model PSF is needed. -> Extracted PSF using [PSFEx](https://www.astromatic.net/software/psfex/), and save hdu[1].data[0][0][0] of the python-read model 'psf'.
3. 

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



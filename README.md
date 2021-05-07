GSI/EnKF WRFIO library
---------------------------------------------------------------

## Build under the hpc-stack umbrella

This can be built under the NOAA hpc-stack (https://github.com/NOAA-EMC/hpc-stack).

- If the only goal is to build GSI/EnKF, one can clone the hpc-stack code from this fork https://github.com/comgsi/hpc-stack where customized config_comgsi.sh and stack_comgsi.sh are provided to build only those libraries required by GSI/EnKF.

- To use the authoritative NOAA hpc-stack and add the gsiwrfio libary, you can follow changes shown here https://github.com/comgsi/hpc-stack/compare/f53255a..a639980

Once completed, you can follow the hpc-stack practices to use `module load gsiwrfio/1.0.0` to set gsiwrfio related environmental variables.

## Build independently
You can also elect to build the gsiwrfio library independently as follows and set the `GSIWRFIO_LIB` environmental variable to let GSI/EnKF know where to find the gsiwrfio library.

```
git clone https://github.com/comgsi/gsiwrfio.git
(... make sure your environment has a valid compiler, mpi and netcdf ...)
cd gsiwrfio
mkdir build
cd build
cmake ..
make -j2
```

Once completed, you will find `libgsiwrfio.a` under `build/src/`

Run the following command to set the `GSIWRFIO_LIB` environmental variable before build GSI/EnKF:

`export GSIWRFIO_LIB="/path/to/libgsiwrfio.a"`   # use setenv for csh-type shells 

### NOTE: You will need latest GSI/EnKF code (after 05/16/2021) to use the gsiwrfio library.

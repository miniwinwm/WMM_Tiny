# WMM_Tiny

This is a small embedded C99 implementation of the World Magnetic Model published by NOAA for calculating the magnetic field at any point on the world's surface for a given date. This implementation uses the latest coefficients from NOAA for the years 2020 to 2025.

This implementation is a cut down version of the source code supplied by NOAA and is intended for small embedded systems. The limitations are:

- Calculates magnetic variation only

- Only calculates the magnetic variation at altitude xero relative to the WGS84 ellipsoid, which is approximately the Earth's surface

- Uses floats in its calculations, not doubles. This will reduce accuracy very slightly.

- Stores the coefficients in a compressed format. The floating point coefficients are converted to fixed point integers and then stored as variable length integers.

The intention of this project is to reduce the code space as much as possible at the expense of RAM. This makes it suitable for embedded processors short on code memory but with ample RAM. The coefficients are compressed in code but are expanded back into their normal format in RAM when the code runs.

This example project is for the STM32F103C8 processor and a project is supplied for the STM32CubeIDE. However, the WMM part of the code is written in standard C99 and can be ported to other processors easily. The files necessary for porting are these:

Core/Inc/wmm.h
Core/Src/wmm.c
Core/Src/WMM_COF.c

Doxygen style documentation of the API is found in wmm.h. Example code calling the API is found in Core/Src/main.c.

This code requires 4.2 kBytes of RAM permanently. All memory is statically allocated.

The source code may look a bit strange to a seasoned C programmer with gotos in the code. This is because this is a port of the WMM souce code provided by NOAA which is itself a port of the original WMM code written in Fortran.

Under folder wmm_cof_converter is a sub-project that compresses the coefficients file supplied by NOAA (WMM.COF) to a C99 source file that is used by the WMM_Tiny project. This sub-project also has project files allowing it to be loaded and built in STM32CubeIDE or the single C99 source file wmm_cof_converter.c can be compiled by any C99 compiler.





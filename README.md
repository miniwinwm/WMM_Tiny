# WMM_Tiny

This is a small implementation of the World Magnetic Model published by NOAA for calculating the magnetic field at any point on or above the world's surface for a given date. This implementation uses the lates coefficients from NOAA for the years 2020 to 2025.

This implementation is a cut down version of the source code supplied by NOAA and is intended for small embedded systems. The limitations are:

- Calculates magnetic variation only

- Only calculates the magnetic variation at the ellipsoid which is approximately the Earth's surface

- Uses floats in its calculations, not doubles. This will redice accuracy very slightly.

- Stores the coefficients in a compressed format. The floating point coefficients are converted to fixed point integers and then stored as variable length integers.

The intention of this project is to reduce the code space as much as possible at the expense of RAM. This makes it suitable for embedded processors short on code memory but with ample RAM. The coefficients are compressed in code but are expanded back into their normal format in RAM when the code runs.

This example project is for the STM32F103C8 processor and a project is supplied for the STM32CubeIDE. However, the WMM part of the code is written in standard C99 and can be ported to other processors easily.

This code requires 4.2 kBytes of RAM permanently. All memory is statically allocated.

Under folder wmm_cof_converter is a sub-project that compresses the coefficients file supplied by NOAA (WMM.COF) to a C source file that is used by the WMM_Tiny project. This sub-project also has project files allowing it to be loaded and built in STM32CubeIDE or the single c file wmm_cof_converter.c can be compiled by any C99 compiler.





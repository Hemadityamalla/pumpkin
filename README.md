#### I took the stuff from the guy below. He does not seem to be maintaining it anymore. 


#### Copyright (c) 2013-2015 Aram H Markosyan. All rights reserved.
#####
##### This file is part of PumpKin (see http://www.pumpkin-tool.org).
##### Please see the COPYRIGHT_and_LICENSE file for the copyright notice, 
##### disclaimer, contact information and the GNU Lesser General Public License.
#####
##### PumpKin is free software; you can redistribute it and/or modify it under the
##### terms of the GNU General Public License (as published by the Free Software 
##### Foundation) version 2.
#####
##### PumpKin is distributed in the hope that it will be useful, but WITHOUT ANY 
##### WARRANTY; without even the IMPLIED WARRANTY OF MERCHANTABILITY or FITNESS 
##### FOR A PARTICULAR PURPOSE.  See the terms and conditions of the GNU General
##### Public License for more details.
#####
##### You should have received a copy of the GNU Lesser General Public License
##### along with this program; if not, write to the Free Software Foundation,
##### Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA
###############################################################################

Download
=================================

Before installing PumpKin, the user should have installed the GLPK package. 
For this we recommend tools like MacPorts (www.macports.org) or 
Fink (www.finkproject.org) for Mac OS X and package management systems for
GNU/Linux distributions. The windows user can get installation instructions 
at (winglpk.sourceforge.net).


The full source code of PumpKin is available at:

http://www.pumpkin-tool.org

After the download user should do:

	1. Copy the pumpkin distribution file to a working directory.
	2. Unpack the distribution file with the following command:
           $ gzip -d pumpkin-X.Y.tar.gz
	After unpacking the distribution file is automatically renamed to ‘pumpkin- X.Y.tar’.
	3. Unarchive the distribution file with the following command: 
			$ tar -x < pumpkin-X.Y.tar
	It automatically creates the subdirectory ‘pumpkin-X.Y’ containing the pumpkin distribution.



Description of this Package
=================================

The PumpKin package contains the folling files:

Copyright_and_License
README
User manual.pdf
src/
	Makefile
	PumpKin.cpp	
	pk_Array.h	
	pk_IO.cpp	
	pk_Pathways.cpp	
	pk_Print.cpp
	pk_Array.cpp	
	pk_DataTypes.h	
	pk_IO.h		
	pk_Pathways.h	
	pk_Print.h
	Examples/
		ZDPlasKin/
			Input_10/
				input.txt		
				qt_conditions_list.txt	
				qt_matrix.txt		
				qt_reactions_list.txt
				qt_conditions.txt	
				qt_densities.txt	
				qt_rates.txt		
				qt_species_list.txt	
			Input_20/
				input.txt		
				qt_conditions_list.txt	
				qt_matrix.txt		
				qt_reactions_list.txt
				qt_conditions.txt	
				qt_densities.txt	
				qt_rates.txt		
				qt_species_list.txt
		Global_Kin/

--------------------------------------

The package consists of the following C++ files:

PumpKin.cpp
pk_DataTypes.h
pk_Array.h, 		pk_Array.cpp
pk_IO.h, 			pk_IO.cpp
pk_Print.h, 		pk_Print.cpp
pk_Pathways.h,		pk_Pathways.cpp

--------------------------------------

a. PumpKin.cpp 			-- is the user defined file to run PumpKin and make output. 
b. pk_DataTypes.h 		-- contains all the abstract structures which store the data like rates etc.
c. pk_Array.h(.cpp) 	-- multidimensional  dynamic array structures
d. pk_IO.h(.cpp)		-- contains all the input routines to read input data 
e. pk_Print.h(.cpp) 	-- contains all the printing (output) routines 
g. pk_Pathways.h(.cpp)  -- performs all operations over pathways. The core of algorithm is implemented in these files.



PumpKin Installation Information
=================================

The simplest way to build this package is:

  1. `cd' to the directory containing the package's source code:
  		$ cd pumpkin-X.Y/src

  2. Type make to buid it:
  		$ make

To run simple examples provided with package type:
		$ ./pumpkin Examples/ZDPlasKin/Input_10
		$ ./pumpkin Examples/ZDPlasKin/Input_20
	or
		$ ./pumpkin Examples/Global_Kin


Possible sources of error while compilation
=================================================
- On fedora 32, 64bit arch, i5 10th Gen Dell Inspiron: The original Makefile (when downloading the package from Aram's website) has the following on line 23:
`$(LINK) $(LFLAGS) -std=gnu++0x $(OBJ) -o $@ $(LIBS)`
where `$(LFLAGS) = -stdlib=libc++`. 

This line gives me an error. I found the solution here: https://stackoverflow.com/questions/34654682/unrecognized-command-line-option-stdlib-libc-gcc-homebrew-gcc-5-3-0-5-3-0

- I had to install glpk (GNU Linear Programming Kit). Earlier I installed the ix86 version. This gave me an error saying that my libglpk.so is incompatible. I found the solution in: https://stackoverflow.com/questions/53668578/skipping-incompatible-directory-gcc . Basically, reinstalling the x86_64 version of ligglpk.so using the dnf dragrora software manager fixed the problem.




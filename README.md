#CppProjectTools

Simple toolset to build projects with C++. This repository stores different small scripts and tools which
could be useful for C++ projects. It'll grow from time to time.

##C++ Makefile

This is a simple makefile which can be used for each common C++ project that creates a final executable.
You only have to put this file into your project, define some options within the makefile which are related
to your project and you're ready to go. Here some details:

###Requirements

As long as you have the GNU compiler and GNU make installed everything might be ready that you're able to
compile your project.

In case you want to use unit testing, you have to install CppUnit:

**CppUnit v1.12.1:** [http://sourceforge.net/projects/cppunit/](http://sourceforge.net/projects/cppunit/)

To able to use the experimental memory check option you need to have Valgrind installed:

**Valgrind:** [http://valgrind.org/](http://valgrind.org/)

###File And Folder Structure

To be able to use it for your project you need to provide following file structure:
* **Src**
	* Stores all header and source files, it's also possible to store your header files in a separated folder, you have to change the common compiler settings that the compiler still knows where it finds those files.
* **makefile** 
	* This makefile.

Following files/folders will be generated automatically by this makefile:

* **Tmp**
	* Stores all generated object files.
* **NameOfExecutable**
	* Your final executable file. The name depending on the project title.
* **NameOfExecutableTest**
	* Unit test executable file. Also here the name depends on the project title, only the term "Test" will be append to the title.
                           
###Options
Following options are available:
* **build-executable** 
	* Default option which will be executed in case of no parameter were defined for this makefile. It compiles all source file to the final executable.
* **test** 
	* Compiles source files, including testing source files to unit test executable which will perform all test suites. For this it's necessary that CppUnit is installed!
* **clean** 
	* Removes main executable, unit test exectuable and the entire Tmp folder.
* **leakcheck** 
	* Performs application with leakcheck to detect memory leaks. This option is still experimental. So it might be not working like expected. Valgrind has to be installed!
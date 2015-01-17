##
# C++ Project Makefile.
#
# This makefile is build for C++ project based on GNU compiler.
# To be able to use it for your project you need to provide following file structure:
#   - Src       -> stores all header and source files, it's also possible to store your header
#                  files in a separated folder, you have to change the common compiler settings
#                  that the compiler still knows where it finds those files
#   - makefile  -> this makefile
#
# Following files/folders will be generated automatically by this makefile:
#   - Tmp                   -> stores all generated object files
#   - NameOfExecutable      -> your final executable file. The name depending on the project title.
#   - NameOfExecutableTest  -> unit test executable file. Also here the name depends on the project title,
#                              only the term "Test" will be append to the title.
#
# Following options are available:
#   - build-executable  -> Default option which will be executed in case of no parameter were defined for this makefile.
#                          It compiles all source file to the final executable.
#   - test              -> Compiles source files, including testing source files to unit test executable which will
#                          perform all test suites. For this it's necessary that CppUnit is installed!
#   - clean             -> Removes main executable, unit test exectuable and the entire Tmp folder.
#   - leakcheck         -> Performs application with leakcheck to detect memory leaks. This option is still
#                          experimental. So it might be not working like expected. Valgrind has to be installed!
#
# LICENSE FOR THIS MAKEFILE:
#
#   The MIT License (MIT)
#
#   Copyright (c) 2013-2015 by Andy Liebke. All rights reserved. (http://andysmiles4games.com)
#
#   Permission is hereby granted, free of charge, to any person obtaining a copy
#   of this software and associated documentation files (the "Software"), to deal
#   in the Software without restriction, including without limitation the rights
#   to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
#   copies of the Software, and to permit persons to whom the Software is
#   furnished to do so, subject to the following conditions:
#
#   The above copyright notice and this permission notice shall be included in
#   all copies or substantial portions of the Software.
#
#   THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
#   IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
#   FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
#   AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
#   LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
#   OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
#   THE SOFTWARE.
#
# @author       Andy Liebke<coding@andysmiles4games.com>
# @version      1.6.1 04-Jan-15
# @copyright    Copyright (c) 2013-2015 by Andy Liebke. All rights reserved. (http://andysmiles4games.com)
#

##
# OPTIONS WHICH HAVE TO BE DEFINED PER EACH PROJECT!
#	

# title of the executable
APP_TITLE = NameOfExecutable

# list of all common source files which have to be defined for creating the
# main executable as well as the unit test executable
# example:
#	Tmp/YourMainFile.o - this is the path to the resulting object file of the source file Src/YourMainFile.cpp
LIST_OBJECTS_COMMON =	

# list of all files which are only necessary for the final executable
LIST_OBJECTS_APP = 

# list of all files for the unit test executable
LIST_OBJECTS_TEST = 

# debugging options
DEBUG_SETTINGS = -g -D_DEBUG

# common and linker specific configuration for the executable
COMMON_SETTINGS = $(DEBUG_SETTINGS) -Weffc++ -Wall -I Src/
LINKER_SETTINGS = 

# common and link specific configuration for the unit test executable
COMMON_TEST_SETTINGS = -D_UNITTEST $(COMMON_SETTINGS)
LINKER_TEST_SETTINGS = -lcppunit
		
##
# CHANGES AREN'T NECESSARY FOR ANYTHING BELOW THIS LINE!
#		
		
.PHONY: build-executable
build-executable: $(LIST_OBJECTS_COMMON) $(LIST_OBJECTS_APP)
	g++ $(COMMON_SETTINGS) $(LINKER_SETTINGS) -o $(APP_TITLE) $^
	
Tmp/Test/%.o: Src/Test/%.cpp
	@mkdir -p $(dir $@)
	g++ $(COMMON_TEST_SETTINGS) -c $^ -o $@

Tmp/%.o: Src/%.cpp
	@mkdir -p $(dir $@)
	g++ $(COMMON_SETTINGS) -c $^ -o $@ 

.PHONY: test
test: $(LIST_OBJECTS_COMMON) $(LIST_OBJECTS_TEST) 
	@g++ $(COMMON_TEST_SETTINGS) $(LINKER_SETTINGS) $(LINKER_TEST_SETTINGS) -o $(APP_TITLE)Test $^
	@echo "Running test cases..."
	@./$(APP_TITLE)Test

.PHONY: start
start:
	@./$(APP_TITLE)

.PHONY: clean
clean:
	rm -rf Tmp/
	rm -f $(APP_TITLE)
	rm -f $(APP_TITLE)Test
	
.PHONY: leakcheck
leakcheck:
	rm -f *.log
	rm -rf *.dSYM
	valgrind --leak-check=full -v --track-origins=yes --log-file=$(APP_TITLE)-Mem.log --dsymutil=yes ./$(APP_TITLE)
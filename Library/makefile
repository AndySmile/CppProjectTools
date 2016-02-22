##
# C++ Library Project Makefile.
# 
# This makefile is build for C++ project based on GNU compiler.
# To be able to use it for your project you need to provide following file structure:
#	- Include 	-> stores all header files which are also for public usage when using this library
#					in your application
#   - Source    -> stores all source files
#   - makefile  -> this makefile
#
#
# LICENSE FOR THIS MAKEFILE:
#	
#   The MIT License (MIT)
#
#   Copyright (c) 2013-2016 by Andy Liebke. All rights reserved.
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
# @author	    Andy Liebke <coding@andysmiles4games.com>	
# @version	    1.8.0 22-Feb-16
# @copyright    Copyright (c) 2013-2016 by Andy Liebke. All rights reserved. (http://andysmiles4games.com)
# 

##
# OPTIONS YOU HAVE TO BE DEFINED IN EACH PROJECT!
#

# title of your library
LIB_TITLE = 

# list of all your files: Tmp/your-cpp-file-with-o-extension.o
LIST_OBJECTS = 	

# debugging options
DEBUG_SETTINGS =  -g -D_DEBUG

# common and linker specific configuration
COMMON_SETTINGS = $(DEBUG_SETTINGS) -Wall -pedantic-errors -Weffc++ -ansi -I Include/
LIBRARY_SETTINGS = 

##
# CHANGE THOSE SETTINGS ONLY IF YOU WORK IN A DIFFERENT DEVELOPMENT ENVIRONMENT!
#
CONFIG_COMPILER = g++
		
##
# CHANGES AREN'T NECESSARY FOR ANYTHING BELOW THIS LINE!
#

.PHONY: build
build: $(LIST_OBJECTS)
	$(CONFIG_COMPILER) -shared -fPIC $(LIBRARY_SETTINGS) -o lib$(LIB_TITLE).a $^
	mkdir -p ./../Lib
	mv ./lib$(LIB_TITLE).a ./../Lib/lib$(LIB_TITLE).a
	rm -rf ./../Incude/*
	cp -r ./Include/* ./../Include
	@echo ">>> DONE!"
	
Tmp/%.o: Source/%.cpp
	@mkdir -p $(dir $@)
	$(CONFIG_COMPILER) $(COMMON_SETTINGS) -c $^ -o $@ 

.PHONY: clean
clean:
	rm -rf ./Tmp
	rm -f ./lib$(LIB_TITLE).a
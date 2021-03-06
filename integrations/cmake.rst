.. _cmake:

CMake
_____


|cmake_logo|


If you are using *CMake* to build your project, you can use the *cmake* generator to manage all your requirements.


**conanfile.txt**

.. code-block:: text

   ...
   
   [generators]
   cmake


When **conan install** is executed, a file named ``conanbuildinfo.cmake`` is created. 

We can include ``conanbuildinfo.cmake`` in our project's ``CMakeLists.txt`` to manage our requirements.


This is the ``CMakeLists.txt`` file we used in the :ref:`Getting started<getting_started>` example:

.. code-block:: cmake

   project(FoundationTimer)
   cmake_minimum_required(VERSION 2.8)

   include(conanbuildinfo.cmake)
   conan_basic_setup()
   
   add_executable(timer timer.cpp)
   target_link_libraries(timer ${CONAN_LIBS})
   

- **include(conanbuildinfo.cmake)** will include the file generated by our **cmake** [generator]
- **conan_basic_setup()** call will asign to **CMake** all the needed variables for linking with our requirements. 
- **${CONAN_LIBS}** contains the libraries to link with. So TARGET_LINK_LIBRARIES, works just fine.


Let's take a look at the generated ``conanbuildinfo.cmake`` file:


.. code-block:: cmake

    set(CONAN_POCO_ROOT "/home/laso/.conan/data/Poco/1.6.1/lasote/stable/package/afafc631e705f7296bec38318b28e4361ab6787c")
    set(CONAN_INCLUDE_DIRS_POCO "/home/laso/.conan/data/Poco/1.6.1/lasote/stable/package/afafc631e705f7296bec38318b28e4361ab6787c/include")
    set(CONAN_LIB_DIRS_POCO "/home/laso/.conan/data/Poco/1.6.1/lasote/stable/package/afafc631e705f7296bec38318b28e4361ab6787c/lib")
    set(CONAN_BIN_DIRS_POCO "/home/laso/.conan/data/Poco/1.6.1/lasote/stable/package/afafc631e705f7296bec38318b28e4361ab6787c/bin")
    set(CONAN_LIBS_POCO PocoUtil PocoXML PocoJSON PocoMongoDB PocoNet PocoCrypto PocoData PocoDataSQLite PocoZip PocoFoundation pthread dl rt)
    set(CONAN_DEFINES_POCO -DPOCO_STATIC=ON
                -DPOCO_NO_AUTOMATIC_LIBS)
    set(CONAN_CXX_FLAGS_POCO "")
    set(CONAN_SHARED_LINK_FLAGS_POCO "")
    set(CONAN_EXE_LINKER_FLAGS_POCO "")
    set(CONAN_C_FLAGS_POCO "")
    
    set(CONAN_ZLIB_ROOT "/home/laso/.conan/data/zlib/1.2.8/lasote/stable/package/3b92a20cb586af0d984797002d12b7120d38e95e")
    set(CONAN_INCLUDE_DIRS_ZLIB "/home/laso/.conan/data/zlib/1.2.8/lasote/stable/package/3b92a20cb586af0d984797002d12b7120d38e95e/include")
    set(CONAN_LIB_DIRS_ZLIB "/home/laso/.conan/data/zlib/1.2.8/lasote/stable/package/3b92a20cb586af0d984797002d12b7120d38e95e/lib")
    set(CONAN_BIN_DIRS_ZLIB "/home/laso/.conan/data/zlib/1.2.8/lasote/stable/package/3b92a20cb586af0d984797002d12b7120d38e95e/bin")
    set(CONAN_LIBS_ZLIB z)
    set(CONAN_DEFINES_ZLIB )
    set(CONAN_CXX_FLAGS_ZLIB "")
    set(CONAN_SHARED_LINK_FLAGS_ZLIB "")
    set(CONAN_EXE_LINKER_FLAGS_ZLIB "")
    set(CONAN_C_FLAGS_ZLIB "")
    
    set(CONAN_OPENSSL_ROOT "/home/laso/.conan/data/OpenSSL/1.0.2d/lasote/stable/package/dd8a0e4171607d74dee9fd0c51153a922d849535")
    set(CONAN_INCLUDE_DIRS_OPENSSL "/home/laso/.conan/data/OpenSSL/1.0.2d/lasote/stable/package/dd8a0e4171607d74dee9fd0c51153a922d849535/include")
    set(CONAN_LIB_DIRS_OPENSSL "/home/laso/.conan/data/OpenSSL/1.0.2d/lasote/stable/package/dd8a0e4171607d74dee9fd0c51153a922d849535/lib")
    set(CONAN_BIN_DIRS_OPENSSL "/home/laso/.conan/data/OpenSSL/1.0.2d/lasote/stable/package/dd8a0e4171607d74dee9fd0c51153a922d849535/bin")
    set(CONAN_LIBS_OPENSSL ssl crypto dl)
    set(CONAN_DEFINES_OPENSSL )
    set(CONAN_CXX_FLAGS_OPENSSL "")
    set(CONAN_SHARED_LINK_FLAGS_OPENSSL "")
    set(CONAN_EXE_LINKER_FLAGS_OPENSSL "")
    set(CONAN_C_FLAGS_OPENSSL "")
    
    set(CONAN_INCLUDE_DIRS "/home/laso/.conan/data/Poco/1.6.1/lasote/stable/package/afafc631e705f7296bec38318b28e4361ab6787c/include"
                "/home/laso/.conan/data/OpenSSL/1.0.2d/lasote/stable/package/dd8a0e4171607d74dee9fd0c51153a922d849535/include"
                "/home/laso/.conan/data/zlib/1.2.8/lasote/stable/package/3b92a20cb586af0d984797002d12b7120d38e95e/include" ${CONAN_INCLUDE_DIRS})
    set(CONAN_LIB_DIRS "/home/laso/.conan/data/Poco/1.6.1/lasote/stable/package/afafc631e705f7296bec38318b28e4361ab6787c/lib"
                "/home/laso/.conan/data/OpenSSL/1.0.2d/lasote/stable/package/dd8a0e4171607d74dee9fd0c51153a922d849535/lib"
                "/home/laso/.conan/data/zlib/1.2.8/lasote/stable/package/3b92a20cb586af0d984797002d12b7120d38e95e/lib" ${CONAN_LIB_DIRS})
    set(CONAN_BIN_DIRS "/home/laso/.conan/data/Poco/1.6.1/lasote/stable/package/afafc631e705f7296bec38318b28e4361ab6787c/bin"
                "/home/laso/.conan/data/OpenSSL/1.0.2d/lasote/stable/package/dd8a0e4171607d74dee9fd0c51153a922d849535/bin"
                "/home/laso/.conan/data/zlib/1.2.8/lasote/stable/package/3b92a20cb586af0d984797002d12b7120d38e95e/bin" ${CONAN_BIN_DIRS})
    set(CONAN_LIBS PocoUtil PocoXML PocoJSON PocoMongoDB PocoNet PocoCrypto PocoData PocoDataSQLite PocoZip PocoFoundation pthread dl rt ssl crypto z ${CONAN_LIBS})
    set(CONAN_DEFINES -DPOCO_STATIC=ON
                -DPOCO_NO_AUTOMATIC_LIBS ${CONAN_DEFINES})
    set(CONAN_CXX_FLAGS " ${CONAN_CXX_FLAGS}")
    set(CONAN_SHARED_LINK_FLAGS " ${CONAN_SHARED_LINK_FLAGS}")
    set(CONAN_EXE_LINKER_FLAGS " ${CONAN_EXE_LINKER_FLAGS}")
    set(CONAN_C_FLAGS " ${CONAN_C_FLAGS}")
    set(CONAN_CMAKE_MODULE_PATH "/home/laso/.conan/data/Poco/1.6.1/lasote/stable/package/afafc631e705f7296bec38318b28e4361ab6787c" "/home/laso/.conan/data/zlib/1.2.8/lasote/stable/package/3b92a20cb586af0d984797002d12b7120d38e95e" "/home/laso/.conan/data/OpenSSL/1.0.2d/lasote/stable/package/dd8a0e4171607d74dee9fd0c51153a922d849535" ${CONAN_CMAKE_MODULE_PATH})
    MACRO(CONAN_BASIC_SETUP)
        conan_check_compiler()
        conan_ouput_dirs_setup()
        conan_flags_setup()
        # CMake can find findXXX.cmake files in the root of packages
        set(CMAKE_MODULE_PATH ${CONAN_CMAKE_MODULE_PATH} ${CMAKE_MODULE_PATH})
    ENDMACRO()

   # ... macros code...


As we can see, conan is preparing some variables:

* ``CONAN_INCLUDE_DIRS``: The headers folders from the requirements.
* ``CONAN_LIB_DIRS``: The library folders from the requirements.
* ``CONAN_BIN_DIRS``: The binary folders from the requirements.
* ``CONAN_LIBS``: The name of the libs we have to link with.
* ``CONAN_DEFINES``: Defines, observe that two are defined, POCO_STATIC and POCO_NO_AUTOMATIC_LIBS, that correspond to options.
* ``CONAN_C_FLAGS``: Flags for C. Not specified for Poco nor its requirements.
* ``CONAN_CXX_FLAGS``: Flags for CXX. Not specified for Poco nor its requirements.
* ``CONAN_SHARED_LINK_FLAGS``: Shared flags for CXX. Not specified for Poco nor its requirements.
* ``CONAN_EXE_LINKER_FLAGS``: Exe linker flags for CXX. Not specified for Poco nor its requirements.


Conan also provides the same variables isolated for each requirement, so you can handle the requirements individually:  **CONAN_POCO_ROOT**, **CONAN_INCLUDE_DIRS_POCO**, **CONAN_INCLUDE_DIRS_OPENSSL**,  etc


All these variables are 'injected' to corresponding **CMake** functions/variables *(INCLUDE_DIRECTORIES, LINK_DIRECTORIES, ADD_DEFINITIONS, CMAKE_CXX_FLAGS...etc)* when you call **conan_basic_setup()** in your ``CMakeLists.txt`` file.


Find Packages
=============
**New** in Conan 0.6! Now conan provides automatic support for CMake **find_package** without creating a custom ``FindXXX.cmake`` file for each package (conan 0.5).

Variables **CMAKE_INCLUDE_PATH** and **CMAKE_LIBRARY_PATH** are set with the right requirements paths. CMake **find_library** function will be able to locate the libraries in the package's folders.

So, you can use **find_package** normally:


.. code-block:: cmake

    project(MyHello)
    cmake_minimum_required(VERSION 2.8)
    
    include(conanbuildinfo.cmake)
    conan_basic_setup()
    
    find_package("ZLIB")
    
    if(ZLIB_FOUND)
        add_executable(enough enough.c)
        include_directories(${ZLIB_INCLUDE_DIRS})
        target_link_libraries(enough ${ZLIB_LIBRARIES})
    else()
        message(FATAL_ERROR "Zlib not found")
    endif()


In addition to automatic **find_package** support, **CMAKE_MODULE_PATH** variable is set with your requirements root package paths. You can override the default behavior of any find_package() by creating a ``findXXX.cmake`` file in your package.



.. |cmake_logo| image:: ../images/cmake_logo.png

.. _`conan's boost package`: https://github.com/lasote/conan-boost.git
.. _`conan's zlib package`: https://github.com/lasote/conan-zlib.git

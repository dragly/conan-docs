.. _xcode:


Xcode
_____


|xcode_logo|  

Conan can be integrated with **XCode** in two different ways:

- Using the **cmake** generator to create a **conanbuildinfo.cmake** file.
- Using the **xcode** generator to create a  **conanbuildinfo.xcconfig** file.


With CMake
----------

Check the :ref:`generator<generators>` section to read about the **cmake** generator.
Check the official `CMake docs`_ to find out more about generating Xcode projects with CMake.


.. _`CMake docs`: https://cmake.org/cmake/help/v3.0/manual/cmake-generators.7.html

With the *xcode* generator
--------------------------

You can use the **xcode**  :ref:`generator<generators>` to integrate your requirements in your *Xcode*  project.
This generator creates an ``xcconfig`` file, with all the *include paths*, *lib paths*, *libs*, *flags* etc, that can be imported in your project.


.. |xcode_logo| image:: ../images/xcode_logo.jpg









Open ``conanfile.txt`` and change (or add) the **xcode** generator:

    
.. code-block:: text

   [requires]
   Poco/1.6.1@lasote/stable
   
   [generators]
   xcode

Install the requirements:

.. code-block:: bash

   $ conan install
   
Go to your **Xcode** project, click on the project and select **Add files to**. 

.. image:: ../images/xcode1.png

Choose ``conanbuildinfo.xcconfig`` generated.

.. image:: ../images/xcode2.png

Click on the project again. In the **info/configurations** section, choose **conanbuildinfo** for *release* and *debug*.

.. image::  ../images/xcode3.png

Build your project as usual.

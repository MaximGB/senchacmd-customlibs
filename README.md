SenchaCmd Custom libraries
==========================

An extension to Sencha CMD allowing one to integrate custom external libraries into the build
Provides support for new app.json configuration property **customlibs**.


Installation
============
Create a Sencha CMD application project, open build.xml file and add the following line

<import file="${basedir}/customlibs.xml"/>

**before**

<import file="${basedir}/.sencha/app/build-impl.xml"/>

Now you can use **customlibs** parameter in the _app.json_ - application build configuration file

Usage
=====
**customlibs** option format is the following

    "customlibs" : [{

        // Classpath to add to application classpath list
        "classpath" : "../../../SecnhaCompatibleLibrary/js",

        // Javascript file or files to append/prepend to the resulting JS file
        // the option might be given as an array of objects as well
        "js" : {

            // Path to a file relative to the current project directory or absolute
            "prepend" : "prepend.js",             

            // Path to a file relative to the current project directory or absolute
            "append"  : "append.js"
        },

        // CSS file or files to append to the resulting CSS file
        // the option might be given as an array of objects as well
        "css" : {
            
            // Path to a file relative to the current project directory or absolute
            "path" : "../../../ExtScheduler2.x/resources/css/sch-all-debug.css",

            // Replacement to execute during the concatenation, might be required to properly adjust image/font
            // URLs to new CSS file base directory
            "replace" : {

                // Regular expression given as a string
                "from" : "\\.\\./images",

                // Substitution pattern
                "to"   : "scheduler"
            }
        },

        // Resources to copy
        // the option might be given as an array of objects as well
        "resources" : {

            // Path to a library's resources directory relative to the current project directory or absolute
            "from"    : "../../../ExtScheduler2.x/resources/images/",

            // Destination path
            "to"      : "build/production/${app.name}/resources/scheduler",

            // Glob file patterns to include
            "include" : "*",

            // Glob file patterns to exclude
            "exclude" : ".*"
        }
    }

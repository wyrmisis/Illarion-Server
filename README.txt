 Illarion

Objectives

   Illarion is the online multiplayer roleplaying game that is developed and
   maintained by the Illarion e.V. This repository contains the server 
   application.

Details

   The application in this repository is the Illarion Server. The official
   repository is https://github.com/Illarion-eV/Illarion-Server. The lead
   developer's repository is https://github.com/vilarion/Illarion-Server. 
   It works together with the Illarion Client found at
   https://github.com/Illarion-eV/Illarion-Java.

Standard

   C++20

Requirements

   GCC 10.2
   GNU Make 4.3
   CMake 3.21
   Boost 1.74.0
   PostgreSQL 13.3
   Lua 5.2.4

Dependencies fetched automatically during the build

   Luabind 0.9.1 with some bugfixes from https://github.com/vilarion/luabind/tree/illarion
   libpqxx 7.6.0
   range-v3 0.11.0
   googletest 1.12.0

Build

   mkdir ../build
   cd ../build
   cmake ../<repo dir>
   cmake --build .
   (add -j at the end to use as many threads as possible)

Test

   ctest

Install

   cmake --install

Debian Packaging

   cpack





Additional set up guide for a Windows environment, by Seeja:

Requirements:
    Windows with Docker Desktop and CLion (https://www.jetbrains.com/clion/) installed

How:
    Clone the server code as usual, switch to the branch you are interested in
    Open the server folder in CLion
    In the lower right a small box will appear (see image). Click Clone.
    Wait while the IDE sets the environment up (The IDE pulls the docker container that is used at github to build the server and reopens the project which is now running in the docker container (in docker desktop you'll see a new entry "devcontainer")).
    Open Docker Desktop, show the individual containers of devcontainer, and click on the three little dots at game-server-1; choose View files.
    Drag and drop "scripts" and "maps" to tmp.
    Switch to the  EXEC tab
    sudo mv /tmp/scripts /usr/share/illarion/scripts
    sudo mv /tmp/maps/* /usr/share/illarion/map/import/

Edit & Run Code:
    Edit the code in CLion
    Using the terminal of CLion (lower left) execute the compiling steps described at Illarion-Server:
    mkdir ../build (if not existing)
    cd ../build (if not already there)
    sudo cmake ../workspace
    sudo cmake --build .
    sudo cmake --install .
    sudo illarion /etc/illarion.conf

Connect to the game:
    Start your client and choose user defined server.
    Set the port to the one visible in Docker Desktop (changes if you restart the container / hostpc)
    The relevant port is the first one, before the :3012

Shutdown the client:
    If for some reason your terminal does not accept CMD+C to stop the client:
    Open a second terminal (just click the +)
    type: ps ax | grep illarion
    remember the first number on the same line as "sudo illarion /etc/illarion.conf"
    type: kill the_number

     ______________________________________________________________________

    Last modified: May 10, 2025
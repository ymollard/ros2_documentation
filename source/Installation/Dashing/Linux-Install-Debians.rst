Installing ROS 2 via Debian Packages
====================================

.. contents:: Table of Contents
   :depth: 2
   :local:

Debian packages for ROS 2 Dashing Diademata are available for Ubuntu Bionic.

Resources
---------

* Status Page:

  * ROS 2 Dashing (Ubuntu Bionic): `amd64 <http://repo.ros2.org/status_page/ros_dashing_default.html>`__\ , `arm64 <http://repo.ros2.org/status_page/ros_dashing_ubv8.html>`__
* `Jenkins Instance <http://build.ros2.org/>`__
* `Repositories <http://repo.ros2.org>`__


Setup Locale
------------
Make sure you have a locale which supports ``UTF-8``.
If you are in a minimal environment, such as a docker container, the locale may be something minimal like POSIX.
We test with the following settings.
It should be fine if you're using a different UTF-8 supported locale.

.. code-block:: bash

   sudo locale-gen en_US en_US.UTF-8
   sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
   export LANG=en_US.UTF-8

Setup Sources
-------------

.. include:: ../_Apt-Repositories.rst

.. _Dashing_linux-install-debians-install-ros-2-packages:

Install ROS 2 packages
----------------------

Update your apt repository caches after setting up the repositories.

.. code-block:: bash

   sudo apt update

Desktop Install (Recommended): ROS, RViz, demos, tutorials.

.. code-block:: bash

   sudo apt install ros-dashing-desktop

ROS-Base Install (Bare Bones): Communication libraries, message packages, command line tools.
No GUI tools.

.. code-block:: bash

   sudo apt install ros-dashing-ros-base

Environment setup
-----------------

Sourcing the setup script
^^^^^^^^^^^^^^^^^^^^^^^^^

Set up your environment by sourcing the following file.

.. code-block:: bash

   source /opt/ros/dashing/setup.bash

Install argcomplete (optional)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

ROS 2 command line tools use argcomplete to autocompletion.
So if you want autocompletion, installing argcomplete is necessary.

.. code-block:: bash

   sudo apt install python3-argcomplete

Try some examples
-----------------

In one terminal, set up the ROS 2 environment as described above and then run a C++ ``talker``:

.. code-block:: bash

   ros2 run demo_nodes_cpp talker

In another terminal source the setup file and then run a Python ``listener``:

.. code-block:: bash

   ros2 run demo_nodes_py listener

You should see the ``talker`` saying that it's ``Publishing`` messages and the ``listener`` saying ``I heard`` those messages.
This verifies both the C++ and Python APIs are working properly.
Hooray!

Next steps after installing
---------------------------
Go on with the `tutorials and demos </Tutorials>` to pursue the configuration of your environment, create your own workspace and packages, and learn ROS 2 core concepts.

Troubleshooting
---------------

Troubleshooting techniques can be found `here </Troubleshooting>`.

Uninstall
---------

If you need to uninstall ROS 2 or switch to a source-based install once you
have already installed from binaries, run the following command:

.. code-block:: bash

  sudo apt remove ros-dashing-* && sudo apt autoremove

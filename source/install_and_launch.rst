Installing and Launching the Game
=================================

This section provides instructions for installing and launching the R-Type game.

System Requirements
-------------------

- **Operating System**: macOS, Windows, Linux
- **Dependencies**: Ensure you have the following dependencies installed:
  - C++20 or higher
  - SFML 2.5+
  - A UDP-capable network

Installation Steps
------------------

1. Clone the repository:

   .. code-block:: bash

      git clone https://github.com/yourusername/R-Type.git

2. Build the project using CMake:

   .. code-block:: bash

      cmake -S . -B build
      cd build

3. Run the server:

   .. code-block:: bash

      ./r-type_server [port]

4. Run the game client:

   .. code-block:: bash

      ./r-type_client -ip [ip] -p [port]

Debug Mode
----------

Build the project using CMake with debug:

    .. code-block:: bash

        cmake -S . -B build-debug -DCMAKE_BUILD_TYPE=Debug
        cd build-debug



Multiplayer Setup
-----------------

For multiplayer, ensure you have a stable network connection and that the server is running. Launch the game client with the server's IP address to join a match.

Troubleshooting
---------------

If you encounter any issues during installation or gameplay, consider the following steps:

- **Dependencies**: Verify that all dependencies are correctly installed.
- **Permissions**: Ensure you have the necessary permissions to execute the game.
- **Network**: Check your network connection for multiplayer mode.

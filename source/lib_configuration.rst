Library Configuration
======================

In this project, we use several libraries to manage different parts of the game. We also use **vcpkg** as our package manager to easily install and manage these libraries.

Vcpkg (Package Manager)
-----------------------

We use **vcpkg** as our package manager to simplify the process of installing and managing external libraries. It helps by:

- **Easy Setup**: Installing libraries like SFML and libconfig is much easier with vcpkg. You don’t have to manually download, configure, and build them.
- **Cross-Platform**: vcpkg supports multiple platforms (Windows, macOS, Linux), which makes it easy to maintain the project across different systems.
- **Library Updates**: vcpkg keeps track of library versions, making it simple to update to newer versions without breaking the project.


SFML (Simple and Fast Multimedia Library)
-----------------------------------------

We chose **SFML** for handling all the graphics, input, and audio in our game. SFML is a good fit because:

- **2D Graphics**: R-Type is a 2D game, so SFML's support for 2D rendering makes it perfect for our needs.
- **Cross-Platform**: It works on Windows, macOS, and Linux, which makes it easy to develop and run the game on different operating systems.
- **Simple to Use**: SFML is easier to use than some other graphics libraries, which saves time in development.

SFML also includes built-in features for handling player input, such as detecting key presses and mouse movement, which are essential for the game controls.

Libconfig
---------

We use **libconfig** to handle configuration files in our project. This library helps us store and manage settings or game options. The reasons we chose libconfig are:

- **Lightweight**: It's a simple library that doesn't take up too much space or memory, which is important for keeping the game efficient.
- **Easy to Read/Write**: It uses a format that's easy to read for humans (like JSON or XML), making it simple to update or change settings without much effort.
- **Flexible**: We can easily add new configuration options as the game evolves, without having to rewrite big parts of the code.

Why These Libraries?
--------------------

The reason we use **SFML**, **libconfig**, and **vcpkg** is because they offer a balance between **ease of use** and **performance**. SFML handles the important parts of the game (like graphics and input), libconfig lets us manage game settings simply, and vcpkg makes managing these libraries much easier. Together, they make development faster and more reliable.

Library Configuration
=====================

In this project, we use several libraries to manage different parts of the game. We also use vcpkg as our package manager to easily install and manage these libraries.

Vcpkg (Package Manager)
------------------------
We use vcpkg as our package manager to simplify the process of installing and managing external libraries. It helps by:

- **Easy Setup**: Installing libraries like SFML and TOML is much easier with vcpkg. You don’t have to manually download, configure, and build them.
- **Cross-Platform**: vcpkg supports multiple platforms (Windows, macOS, Linux), which makes it easy to maintain the project across different systems.
- **Library Updates**: vcpkg keeps track of library versions, making it simple to update to newer versions without breaking the project.

.. list-table::
   :header-rows: 1

   * - **X**
     - **vcpkg**
     - **Conan**
     - **Homebrew**
   * - **Platforms**
     - Windows, macOS, Linux
     - Windows, macOS, Linux
     - Mainly macOS, Linux
   * - **Ease of Use**
     - Easy installation with simple commands
     - Configurable but more complex
     - Very simple on macOS
   * - **Version Management**
     - Yes
     - Yes
     - Yes, but less centralized
   * - **Dependency Support**
     - Large selection of libraries
     - Large selection with flexibility
     - Mainly for macOS
   * - **Update Management**
     - Simple and quick to manage
     - More complex
     - Depends on taprooms (repositories)

SFML (Simple and Fast Multimedia Library)
------------------------------------------

We chose SFML for handling all the graphics, input, and audio in our game. SFML is a good fit because:

- **2D Graphics**: R-Type is a 2D game, so SFML's support for 2D rendering makes it perfect for our needs.
- **Cross-Platform**: It works on Windows, macOS, and Linux, which makes it easy to develop and run the game on different operating systems.
- **Simple to Use**: SFML is easier to use than some other graphics libraries, which saves time in development.

| Criterion                | SFML                      | SDL                  | Allegro            |
|--------------------------|---------------------------|----------------------|--------------------|
| **Platforms**             | Windows, macOS, Linux     | Windows, macOS,      | Windows, macOS,    |
|                          |                           | Linux                | Linux              |
| **2D Support**            | Yes                       | Yes                  | Yes                |
| **Built-in Audio**        | Yes                       | Yes                  | Yes                |
| **Ease of Use**           | Very simple               | Relatively complex   | Moderately simple  |
| **Performance for 2D games** | Very good                | Good but slightly heavier | Good, but more focused on simple 2D |


SFML also includes built-in features for handling player input, such as detecting key presses and mouse movement, which are essential for the game controls.

TOML
-----
We use TOML to handle configuration files in our project. This library helps us store and manage settings or game options. The reasons we chose TOML are:

- **Readable Format**: TOML's syntax is designed to be human-readable and easy to edit, making it simple to update or change settings.
- **Lightweight and Flexible**: TOML is compact and doesn't consume too much space or memory, which keeps the game efficient.
- **Compatibility**: TOML's straightforward structure makes it easy to parse and flexible for adding new configuration options as the game evolves.

Cereal (Serialization Library)
-------------------------------
We use cereal for serializing and deserializing messages between components. The reasons we chose cereal include:

- **Lightweight Serialization**: cereal is optimized for performance, which is essential in real-time multiplayer games like ours.
- **Cross-Platform**: It is compatible with multiple platforms, making it adaptable to various development environments.
- **Supports Multiple Formats**: cereal can serialize data in different formats, allowing flexibility in data storage and transmission.

Why These Libraries?
---------------------
The reason we use SFML, TOML, cereal, and vcpkg is because they offer a balance between ease of use and performance. SFML handles the essential parts of the game (like graphics and input), TOML allows us to manage game settings simply, cereal handles serialization efficiently, and vcpkg makes managing these libraries straightforward. Together, they make development faster and more reliable.
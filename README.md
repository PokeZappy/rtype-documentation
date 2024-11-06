# R-Type Game

## Introduction

Welcome to R-Type, a classic side-scrolling shooter game where players control a spaceship, fighting against waves of enemies. This game is designed to be fast-paced, requiring quick reflexes, and features a multiplayer mode, dynamic levels, and engaging gameplay.

## Game Features
- **Multiplayer Mode**: Team up with friends and tackle levels together. Cooperation is key to defeating tough enemies.
- **Dynamic Levels**: Levels are designed to be engaging and challenging, with various enemy placements.
- **Customizable Gameplay**: Highly customizable game engine allowing developers to tweak mechanics, graphics, and network protocols.

## System Requirements

- **Operating System**: macOS, Windows, Linux
- **Dependencies**:
    - C++20 or higher
    - SFML 2.5+
    - A UDP-capable network
    - CMake (for building)
    - Optional: Debugger tools for troubleshooting

## Libraries Used
- **SFML**: Used for rendering 2D sprites, animations, and handling input.
- **Cereal**: For serialization of game data.
- **TOML**: For configuration management.
- **Libconfig**: Configuration library for handling game settings.
- **EventBus**: Manages event-driven communication between systems and components.
- **C++ Standard Library**: Includes containers, algorithms, and threading utilities.

## Installation Instructions

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/R-Type.git
    ```

2. Build the project using CMake:
    ```bash
    cmake -S . -B build
    cd build
    ```

3. Run the game server:
    ```bash
    ./r-type_server [port]
    ```

4. Run the game client:
    ```bash
    ./r-type_client -ip [ip] -p [port]
    ```

## Debug Mode

Build the project using CMake with debug:

```bash
cmake -S . -B build-debug -DCMAKE_BUILD_TYPE=Debug
cd build-debug
```

## Multiplayer Setup

To play multiplayer, ensure you have a stable network connection and that the server is running. Launch the game client with the server’s IP address to join a match.

## Player Controls
- **Move Up**: Use the Z key to move the ship upward.
- **Move Down**: Use the S key to move the ship downward.
- **Move Left**: Use the Q key to move the ship to the left.
- **Move Right**: Use the D key to move the ship to the right.
- **Shoot**: Press the Spacebar to fire your weapons.
- **Launch Game**: Press the L key to start the round.
- **Settings Menu**: Press the Escape key to access the settings.
- **Show Ping**: Press F9 to show the ping.
- **Show Hitbox**: Press the H key to show the hitbox.
- **Scoreboard**: Press the Tab key to view the scoreboard.
- **Exit**: Press Escape to exit the game.

## Game Engine Architecture
The game engine is built using the Entity-Component System (ECS) design pattern, promoting flexibility and reusability. The core components of the engine include:

Rendering Engine: Manages 2D sprite rendering and animations.
- **Physics Engine**: Handles collision detection and response.
- **Input System**: Processes player inputs and translates them into game actions.
- **Networking Module**: Manages real-time communication between clients and the game server.

### Entity-Component System (ECS)
- **Entities**: Objects in the game world (e.g., player, enemies, bullets).
- **Components**: Data containers that hold the properties and state of an entity (e.g., position, health).
- **Systems**: Logic that updates game entities (e.g., movement system, collision system).
- **Event Bus**: Used to publish events like collisions, triggering related systems.

## Troubleshooting

If you encounter issues during installation or gameplay, try the following:

- **Dependencies**: Ensure all required dependencies are installed.
- **Permissions**: Make sure you have the necessary permissions to execute the game files.
- **Network**: Verify your network connection for multiplayer mode.
- **CMake**: Ensure CMake is installed and correctly configured.

##Further Documentation

For more detailed information on how to extend or modify the game, refer to the Doxygen-generated documentation for each component and entity.
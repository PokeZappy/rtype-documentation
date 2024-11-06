Creating a Game with the R-Type Engine
======================================

This guide will help you create a new game using the R-Type game engine. We'll walk through setting up the engine, creating game elements, and adding some basic gameplay features.

Creating Game Elements
----------------------

The engine uses an **Entity-Component System (ECS)** to organize game objects.

- **Entities**: These are things in the game (like players, enemies, bullets).
- **Components**: These are properties of entities (like position, speed, health).
- **Systems**: These are the logic that updates the game (like moving entities or detecting collisions).

### Step 1: Create Entities

Define your game objects (entities). For example, to create a player and enemies:

   ::

      auto player = engine.createEntity();
      auto enemy = engine.createEntity();

### Step 2: Add Components

Give each entity some properties (components). For example, to give a position to a player and enemy:

   ::

      player->addComponent<PositionComponent>(0.0f, 0.0f);
      enemy->addComponent<PositionComponent>(5.0f, 5.0f);

### Step 3: Add Logic with Systems

Add systems that control how entities behave. For example, to create a system for player movement:

   ::

      engine.addSystem<MovementSystem>();

Example: Creating Game Elements
-------------------------------

Here’s a more detailed example where we create a player with health and movement components:

1. Include the engine header file:

   ::

      #include "Engine.hpp"

2. Create a player entity:

   ::

      auto player = engine.createEntity();

3. Define a custom health component or use predefined components if available:

   ::

      class HealthComponent : public potEngine::AComponent {
      public:
          int health = 10;

          HealthComponent() = default;
          ~HealthComponent() = default;
      };

   You can also use built-in components like `PositionComponent`:

   ::

      auto position = std::make_shared<potEngine::PositionComponent>(0.0f, 0.0f);

4. Add components to the player entity:

   ::

      auto health = std::make_shared<HealthComponent>();
      player->addComponent(position);
      player->addComponent(health);

Now we have a `player` entity with position and health. You can add as many components and entities as needed. Once set, you can work with systems to add interactivity.

Making the Game Interactive
---------------------------

### Handling Input

To make the game interactive, use the **Input System** to control the player. For example, to move the player with arrow keys:

   ::

      engine.addSystem<InputSystem>();

### Adding Enemies and Collisions

Create enemy entities and add a collision system to detect interactions between the player and enemies. If a collision happens, you can reduce health or trigger other events.

   ::

      engine.addSystem<CollisionSystem>();

Networking with the Engine
--------------------------

If you want to make your game multiplayer, the engine has a **Networking Module** that enables communication between players and the server.

### Setting Up the Server

1. **Start the Game Server**: The server manages the game state and sends updates to clients.

   ::

      ./rtype-server

2. **Client-Server Communication**: The engine uses the UDP protocol to send messages between the server and clients. You can customize the communication protocol if needed.

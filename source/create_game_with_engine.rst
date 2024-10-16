Creating a Game with the R-Type Engine
======================================

This guide will help you create a new game using the R-Type game engine. We'll walk through setting up the engine, creating game elements, and adding some basic gameplay features.

Creating Game Elements
-----------------------

The engine uses something called **Entity-Component System (ECS)** to organize game objects.

- **Entities**: These are things in the game (like players, enemies, bullets).
- **Components**: These are properties of entities (like position, speed, health).
- **Systems**: These are the logic that updates the game (like moving entities or detecting collisions).

### Step 1: Create Entities

You first need to define your game objects (entities). For example, to create a player and enemies:

   .. code-block:: cpp

      create_entity

### Step 2: Add Components

Next, give each entity some properties (components). For example, you can give them positions or graphics.

   .. code-block:: cpp

      player.components

### Step 3: Add Logic with Systems

Finally, you need to add systems that control how entities behave. For example, you might create a system to move the player when you press a key.

   .. code-block:: cpp

      movement

Example Creating Game Elements
------------------------------

For example, we want to create a player who has health and movement.

1. First of all, we need to include "Engine.hpp"

    .. code-block:: cpp

            #include "Engine.hpp"

2. Then you can create an Entity player

    .. code-block:: cpp

           std::shared<potEngine::AEntity> player = potEngine::engine.createEntity();


3. Create your component in a separate file who will inherit of potEngine::AComponent. For the health Component.

    .. code-block:: cpp
        class HealthComponent: public potEngine::AComponent {
            public:
                _health = 10;

                HealthComponent();
                ~HealthComponent();
        }

    But we provide some default components like the position Component that you can call already using the potEngine like this : potEngine::PositionComponent.


4. Add the component to the player entity. How do we do it ?

    .. code-block:: cpp
        std::shared<potEngine::PositionComponent> position = std::make_shared<potEngine::PositionComponent>(0.0, 0.0);
        std::shared<HealthComponent> position = std::make_shared<HealthComponent>();
        engine.addComponent(player, position);
        engine.addComponent(player, health);


Now we have a entity player that have a position and health. You can add as much components and entities that you want. Now that we have that, we can work with systems to add interactivity.

Making the Game Interactive
----------------------------

### Handling Input

To make the game interactive, you can use the **Input System** to control the player. For example, move the player when pressing the arrow keys.

   .. code-block:: cpp

      input

### Adding Enemies and Collisions

You can create enemy entities and make a system to check for collisions between the player and enemies. If a collision happens, you can reduce health or trigger other events.

   .. code-block:: cpp

      colision

Networking with the Engine
---------------------------

If you want to make your game multiplayer, the engine has a **Networking Module** that allows communication between players and the server.

### Setting Up the Server

1. **Start the Game Server**: The server manages the game state and sends updates to clients (players).

   .. code-block:: bash

      ./rtype-server

2. **Client-Server Communication**: The engine uses the UDP protocol to send messages between the server and clients. You can customize the communication protocol for your game if needed.

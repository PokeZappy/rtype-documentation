Game Engine Documentation
=========================

Our custom-built game engine powers the R-Type game. This section covers the core components of the engine and its architecture.

Engine Components
-----------------

- **Rendering Engine**: Manages 2D sprite rendering, including animations and background elements.
- **Physics Engine**: Handles collision detection and response.
- **Input System**: Processes player inputs on keyboard and translates them into in-game actions.
- **Networking Module**: Manages real-time communication between clients and the game server.

Entity-Component System (ECS)
-----------------------------

The engine uses an Entity-Component System (ECS) architecture, which is a design pattern that promotes flexibility and reusability. Here is an overview of how the ECS works:

- **Entities**: These are the objects in the game world. Each entity is a unique identifier that can have multiple components attached to it.
- **Components**: These are data containers that hold the properties and state of an entity. Components do not contain any behavior.
- **Systems**: These are the logic and behavior of the game. Systems are managed by an event bus. The only condition to subscribe is
- **Events**: A Event is a message that is published by the event bus. The event bus is a singleton that is used to publish events and subscribe to them.

The ECS architecture allows for a clean separation of data and behavior, making it easier to manage and extend the game engine.

Event Bus
---------

The EventBus permit that when a collision is detected, the collision event is published and the consequences is that systems linked to it will be triggered.


Customization
-------------

The engine is highly customizable, allowing developers to tweak gameplay mechanics, graphics, and network protocols.

Further Details
---------------

For more detailed information on each component and entity, refer to the Doxygen-generated documentation.
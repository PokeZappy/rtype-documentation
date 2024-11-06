Network Specification
=====================

This document explains the network protocol used in the R-Type game, focusing on how the client and server communicate using the UDP protocol.

Overview of UDP Protocol
------------------------

The game uses the **UDP** protocol to handle real-time communication. It focuses more on low-latency (speed) rather than ensuring every message gets through. This is important for fast-paced games where delays can mess up the experience.

.. image:: https://i.imgur.com/qHD7yCg.png
   :alt: Definition Protocol UDP
   :align: center

Communication Model
-------------------

The client and server communicate using specific message formats. The client sends its actions to the server, and the server responds with updates about the game state.

Client to Server Protocol
-------------------------

When a client sends a message to the server, it follows this format:

.. code-block:: none

   CLIENT_ID ACTION

### CLIENT_ID

The **CLIENT_ID** is the unique ID for the client on the server. This helps the server track the actions and status of each player.

- **Not Connected**: `0x00`
- **Connected**: IDs go from `0x01` up to the max number of players allowed.

### ACTION

The **ACTION** part tells the server what the client is trying to do. Here are the available actions and their codes:

- **CONNECTION**: `0x01` -- Client asking to connect.
- **DISCONNECT**: `0x02` -- Client asking to disconnect.
- **INFORMATION**: `0x03` -- Client sending information.
- **MOVE_UP**: `0x04` -- Client moving up.
- **MOVE_DOWN**: `0x05` -- Client moving down.
- **MOVE_LEFT**: `0x06` -- Client moving left.
- **MOVE_RIGHT**: `0x07` -- Client moving right.
- **MOVE_SINUSOIDAL**: `0x08` -- Client moving in a sinusoidal pattern.
- **MOVE_TOP_DOWN**: `0x09` -- Client moving from top to down.
- **MOVE_UP_STOP**: `0x0A` -- Client stopping upward movement.
- **MOVE_DOWN_STOP**: `0x0B` -- Client stopping downward movement.
- **MOVE_RIGHT_STOP**: `0x0C` -- Client stopping rightward movement.
- **MOVE_LEFT_STOP**: `0x0D` -- Client stopping leftward movement.
- **COLLISION**: `0x0E` -- Client reporting a collision.
- **DEATH**: `0x0F` -- Client reporting death.
- **START_SHOOT**: `0x10` -- Client starting to shoot.
- **END_SHOOT**: `0x11` -- Client stopping shooting.
- **START_STAGE**: `0x12` -- Client starting a stage.
- **HURDLE**: `0x13` -- Client encountering a hurdle.
- **DHURDLE**: `0x14` -- Client dealing with a hurdle.
- **HIT**: `0x15` -- Client reporting a hit.
- **SHOW_HITBOX**: `0x16` -- Client showing hitbox.
- **UPDATE_SCORE**: `0x17` -- Client updating score.
- **BOBBER**: `0x18` -- Client using bobber.
- **PING**: `0x19` -- Client sending a ping.
- **PONG**: `0x1A` -- Client responding with a pong.
- **DROP**: `0x1B` -- Client dropping an item.
- **RESET**: `0x1C` -- Client resetting the game.

The **CLIENT_ID** and **ACTION** together allow the server to figure out what each player is doing.

Server to Client Protocol
-------------------------

When the server sends a message to the client, it follows this format:

.. code-block:: none

   ENTITY_TYPE ENTITY_ID ACTION PARAMETERS

### ENTITY_TYPE

The **ENTITY_TYPE** shows what kind of entity (object) is involved. This helps the client know whether it’s dealing with a player, enemy, or something else.

- **PLAYER**: The entity is a player character.
- **SHOOT**: The entity is a projectile.
- **MOB**: The entity is an enemy unit (non-player).

### ENTITY_ID

The **ENTITY_ID** is the unique ID for the specific entity, so the client can know exactly which object the server is talking about.

### ACTION

The **ACTION** tells the client what the entity is doing or what has changed. These are the main actions the server sends:

- **MOVE**: The entity should move to a new position.
- **COLLIDE**: The entity has collided with something.
- **LOST_HP**: The entity has lost health.
- **SPAWN**: A new entity should appear.
- **DEAD**: The entity has died and should be removed.

### PARAMETERS

The **PARAMETERS** give extra info about the action. For example:

- **MOVE**: Includes the new `x` and `y` positions as bits.
- **COLLIDE**: Might include details about what was hit.

Client Authentication
----------------------

The **CONNECTION** message is like a handshake between the client and server. Once connected, the client gets a **CLIENT_ID** that it will use for all communication. This helps avoid actions from clients that aren't properly connected.

---

This specification ensures fast, secure, and reliable communication between players and the game server.

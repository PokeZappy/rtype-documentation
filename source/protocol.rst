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
- **MOVE_UP**: `0x03` -- Client moving up.
- **MOVE_DOWN**: `0x04` -- Client moving down.
- **MOVE_LEFT**: `0x05` -- Client moving left.
- **MOVE_RIGHT**: `0x06` -- Client moving right.
- **SHOOT**: `0x07` -- Client firing a projectile.

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

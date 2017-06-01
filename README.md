# Protocol

The protocol used by Insecticide for communication between servers and clients.

__Please note: The Protocol is still evolving and might change drastically between iterations.__

## Commands

### Server Commands

#### `INIT`

The `INIT` command is the first command sent from the server after connection has been established to a client. It prompts the client to send information, about the debugged project's path and ID.

#### `STEPIN`

The `STEPIN` command prompts the client to step into functions. The client should respond with `OK` after the next code step has been processed and stopped.

#### `GETSTACK`

The `GETSTACK` command requests the current stack traceback from the client.

#### `GETVARIABLES`

The `GETVARIABLES` command requests the serialized scope of the current state from the client.

### Client Responses

Each succesful response from the client is prefixed by the `OK` command followed by additional values dependent on the original command. These values should be separated by semicolons `;`.

#### To `INIT`  

Upon receiving the `INIT` command, the client should respond with the debug project's ID and the path to `Insecticide.lua`.

##### _Example:_

`OK;03708201;/lib/debug/Insecticide.lua`

#### To `STEPIN`

After successfully stepping into code, the client returns no additional values to the server.

##### _Example:_

`OK`

#### To `GETSTACK`

WIP
##### _Example:_

`OK,main.lua:love.load:2;src/other.lua:loadAssets:24`

#### To `GETVARIABLES`

WIP

##### _Example:_

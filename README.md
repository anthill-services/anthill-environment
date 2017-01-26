## Environment Service
This service solves two problems:

1. There should be one well-known location to start communication from
2. Production environment should be divided from development with no side effects

### A Starting Point
When the game starts, it should know where the actual services located, to communicate with. That's why each game has a well-known address of the Environment Service hardcoded in it. So other services can move without side effects.

### A Sandbox
While the game is being developed, usually it runs on special development environment to ensure the real players are not affected. And eventually, should be switched to production. However, usually the "environment switch" would require a new game build with new environment information. Yet every new build should be tested before shipping ... in development environment.

That's why the game hardcodes only these things:

1. Environment Location (e.g. `https://environment.example.com`)
2. Game Name (e.g. `thegame`) and Game Version (e.g. `1.0`)

That's where the service kicks in: the actual environment is based on the version information, server side.
<br><br>
<div align="center"><img src="https://cloud.githubusercontent.com/assets/1666014/22352370/8214fb22-e424-11e6-80d6-f1ba3c863dc9.png" height="241"/>
<br>
Environments or Game Versions could be configured at <a href="https://github.com/anthill-services/anthill-admin">Admin Service</a>.
</div>
<br><br>
At the end of the day, the Environment Service points client application to the right <a href="https://github.com/anthill-services/anthill-discovery">Discovery Service</a> location (based on the environment).

### Customization
Each environment could have custom variables defined, completely game-specific.

# API
Please refer to the <a href="https://github.com/anthill-services/anthill-environment/wiki/API">API Documentation</a> for more information.
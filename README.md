# HubSockets-Client
A TypeScript HubSockets npm package to be used with the C# server-side HubSockets nuget package.  
Repo: https://github.com/sladewasinger/HubSockets-Client  

### Server
https://github.com/sladewasinger/HubSockets    
  
  
# Usage:
## Connecting:
```typescript
import { HubSocketService } from 'hubsockets-client';

hubSocketService = new HubSocketService();
await hubSocketService.doConnect(
'wss://' + window.location.hostname + ':443/ws'
);
```

## Listen for Events:
```typescript
hubSocketService
    .listenOn<GameState>('GameStateUpdated')
    .subscribe((x) => this.gameStateUpdated(x));
```

## Send with response as promise:

```typescript
const hubResponse = await this.hubSocketService
        .sendWithPromise<HubResponse<number>>('GetTotalPlayerCount', {});
const count = hubResponse.data;
```

## Send without expecting a response:
```typescript
hubSocketService.send('Clear', '');
```

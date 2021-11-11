# Paella Player life cycle

Once we create the Paella Player instance, it can be in three load states:

- Unloaded: The Paella Player instance is created. In this state all static parameters of the player are defined (configuration, available plugins, etc.).
- Manifest loaded: In this state the configuration, dictionaries, video manifest and some types of early loading plugins (data, keyboard shortcuts, event tracking and the like) have been loaded.
- Loaded: In this state, the video streams, the video layout plugins, the user interface and the rest of the plugins are loaded.

## Switch player state

There are different cases in which it is useful to switch between these states, for example, in SPA applications where we want to reload a different video, or in long lists of videos where we want to download some of them to free resources.

They are several APIs with which we can move between theese states:

![img/paella-player-states.svg](img/paella-player-states.svg)

Note: check Paella Player initialization [here](initialization.md).

```javascript
import { Paella, PlayerState, PlayerStateNames } from 'paella-core';

...

const player = new Paella('container-id', initData);

console.log(PlayerStateNames[player.state]);    // UNLOADED

await player.loadManifest();
console.log(PlayerStateNames[player.state]);    // MANIFEST

await player.loadPlayer();
console.log(PlayerStateNames[player.state]);    // LOADED

await player.unloadPlayer();
console.log(PlayerStateNames[player.state]);    // MANIFEST

await player.unloadManifest();
console.log(PlayerStateNames[player.state]);    // UNLOADED

// Load and unload paella player in one step
await player.load();
console.log(PlayerStateNames[player.state]);    // Loaded

await player.unload();
console.log(PlayerStateNames[player.state]);    // Unloaded

// Reload paella player
await player.reload();
```

If you are using Paella Player in a SPA application (see [paelle player react](paella_react.md) or [paella player svelte](paella_svelte.md) for more information), you can use the `reload()` function to unload the player, do some action and reload it again. You can specify the action as a parameter using a function that can be asynchronous if you need it:

```javascript
await player.reload(() => {
  // This code is executed fater unload the player,
  // and before loading it again
  localtion.hash = 'id=other-video-id';
})
```

## Life cycle exceptions

There are certain functions that can only be called in a specific state:

<table>
  <tr>
    <th>Function</th>
    <th>Required state</th> 
  </tr>
  <tr>
    <td>`load()`</td>
    <td>`PlayerState.UNLOADED`</td> 
  </tr>
  <tr>
    <td>`unload()`</td>
    <td>`PlayerState.LOADED`</td> 
  </tr>
  <tr>
    <td>`loadManifest()`</td>
    <td>`PlayerState.UNLOADED`</td> 
  </tr>
  <tr>
    <td>`loadPlayer()`</td>
    <td>`PlayerState.MANIFEST`</td> 
  </tr>
  <tr>
    <td>`unloadManifest()`</td>
    <td>`PlayerState.MANIFEST`</td> 
  </tr>
  <tr>
    <td>`unloadPlayer()`</td>
    <td>`PlayerState.LOADED`</td> 
  </tr>
</table>

If any of these functions are used in an unsuitable state, Paella Player will throw an exception.
# HKOSCon2017 Haxe Game Workshop

[![Join the chat at https://gitter.im/hkoscon2017-haxe-game/Lobby](https://badges.gitter.im/hkoscon2017-haxe-game/Lobby.svg)](https://gitter.im/hkoscon2017-haxe-game/Lobby?utm_source=badge&utm_medium=badge&utm_content=badge)

Workshop info: [Build a cross-platform game in Haxe](https://hkoscon.org/2017/topics/build-a-cross-platform-game-in-haxe/)

This is an [agar.io](https://agar.io/) clone to demonstrate the capability of Haxe in building cross platform games,
where codes are shared among multiple game platforms (web, mac, windows, android & ios),
as well as between game client and game server for multiplayer games.

## Preparation

Participants should have programming experience with at least one programming language. Proficiency with JavaScript, Java, or C# is ideal, but experience with other languages such as C/C++, Python, or Ruby is also sufficient. Participants should have some familiarity using the command line. Participants should bring their own laptop computer, with either Windows, Mac, or Linux installed.

Please follow the instruction listed below before the workshop, such that you can progress smoothly.

### Install Haxe

Get Haxe from http://haxe.org/download/.

### Install Node.js

Get Node.js from https://nodejs.org/, and optionally [yarn](https://yarnpkg.com/).

### Install Haxe Libraries

 * [Luxe](https://luxeengine.com). According to the instruction at https://luxeengine.com/get/:

   ```bash
   haxelib install snowfall
   haxelib run snowfall update luxe
   ```

 * [haxe-ws](https://github.com/soywiz/haxe-ws)

   ```bash
   haxelib install haxe-ws
   ```

 * [hxnodejs](https://github.com/HaxeFoundation/hxnodejs)

   ```bash
   haxelib install hxnodejs
   ```


### Install Visual Studio Code

Although in theory you can use any [IDE or text editor](https://haxe.org/documentation/introduction/editors-and-ides.html), we recommend using [Visual Studio Code](https://code.visualstudio.com/) with the [Haxe Extension Pack](https://marketplace.visualstudio.com/items?itemName=vshaxe.haxe-extension-pack), which offers the best Haxe support at the moment.

### Install C++ development tools

(Optional, for building native targets, e.g. mac, windows, linux, ios, android)
Depending on your OS, [Visual Studio](https://www.visualstudio.com/) (Windows), [XCode](https://developer.apple.com/xcode/) (Mac), or gcc (Linux).

## Notes

We will introduce Haxe and go through creating a simple multi-player game during the workshop together. The instruction will be given during the workshop. Below is some notes for future reference.

### Server

```bash
haxe server.hxml
cd bin/server
npm install ws # or `yarn add ws`
node server.js
```

### Client

```bash
haxelib run flow run web
haxelib run flow run mac
haxelib run flow run windows
```

To give proper code completion, VS Code needs a hxml file, which can be generated by
```
haxelib run flow info [web|windows|mac|linux] --hxml > client.hxml
```
See https://github.com/vshaxe/vshaxe/wiki/Framework-Notes#snow.

### Shared Code

The `World` class contains the core game logic.
When the game is set to single-player mode, the `World` is run in the client.
In other words, the same piece of Haxe code for the `World` class is compiled into different platforms
(web, mac, windows, android, & ios).
When the game is in multi-player mode, the `World` is run on the server. Again, the same piece of 
Haxe code for the `World` class is compiled into the server language (nodejs for our choice here).

The `Command` and `Message` enums represents the protocol between the client and server in multiplayer
mode. The same piece of code is used in both client and server.

## Feedback / Questions

Feel free to [open issues](https://github.com/kevinresol/hkoscon2017-haxe-game/issues) or contact us directly.

## License

<p xmlns:dct="http://purl.org/dc/terms/" xmlns:vcard="http://www.w3.org/2001/vcard-rdf/3.0#">
  <a rel="license"
     href="http://creativecommons.org/publicdomain/zero/1.0/">
    <img src="https://licensebuttons.net/p/zero/1.0/88x31.png" style="border-style: none;" alt="CC0" />
  </a>
  <br />
  To the extent possible under law,
  <span resource="[_:publisher]" rel="dct:publisher">
    <span property="dct:title">Andy Li & Kevin Leung</span></span>
  has waived all copyright and related or neighboring rights to
  <span property="dct:title">"Build a cross-platform game in Haxe" workshop</span>.
This work is published from:
<span property="vcard:Country" datatype="dct:ISO3166"
      content="HK" about="https://github.com/kevinresol/hkoscon2017-haxe-game">
  Hong Kong</span>.
</p>

# cleveranomaly's General Programming Convention
## Preamble
Each programming languages have distinct guidelines for code style. Such difference in code style might potentially increase the difficulty to switch programming languages.<br>
This convention aims to generalize the code style which can be expanded upon and slightly altered for personalization purposes. This convention does not target a specific programming language, meaning with minor modifications and additional personal guidelines, this convention can be applied to various programming languages.

## Object-oriented programming guidelines
<a href="https://wikipedia.org/wiki/Object-oriented_programming"><strong>OOP</strong></a> builds upon the concept of "objects", which can withhold data (and/or code). Data can be represented in multiple forms, including, but not limited to numbers, strings, etc.

### Object Naming Scheme
Objects fall into 2 categories: constant objects (constants, immutable objects) and variable objects (variables, mutable objects).<br>
<table>
  <tr>
    <td><strong>Problem</strong></td>
    <td><strong>Constants</strong></td>
    <td><strong>Variables</strong></td>
  </tr>
  
  <tr>
    <td>Casing</td>
    <td><code>UPPERCASE_SNAKE_CASE<code></td>
    <td><code>lowercase_snake_case</code></td>
  </tr>
  
  <!-- <tr>
    <td></td>
    <td></td>
    <td></td>
  </tr> -->
</table>

Apart from that, selecting the correct characters to precisely name objects is also significant. Take the code sample below for instance:<br>
```ts
declare class Client, Message, Interaction;

const client = new Client({
  "intents": 14079,         // Client intents
  "token": "secret token"   // Client token
});

client.on("messageCreateEvent", (message: Message) => {
  if(message.content === "!ping") message.reply("Pong!");       // If the content is ping then we pong
  else if(message.content === "!pong") message.reply("Ping!");  // If it's pong then we ping
});

client.on("interactionCreateEvent", (interaction: Interaction) => {
  if(interaction.getCommand().name === "ping") interaction.reply("Pong!");      // If the content is ping then we pong
  else if(interaction.getCommand().name === "pong") interaction.reply("Ping!"); // If it's pong then we ping
});

client.authenticate();  // Authenticate
```
The above sample is quite complicated, especially the variable naming. All programmers are advised to keep in mind that the shorter the object names are, the better, given that those objects are not constants. With that said, here is a code sample with shortened name:<br>
```ts
declare class Client, Message;

const client = new Client({
  "intents": 14079          // Client intents,
  "token": "secret token"   // Client token
});

client.on("messageCreateEvent", (m: Message) => {
  if(m.content === "!ping") m.reply("Pong!");       // If the content is ping then we pong
  else if(m.content === "!pong") m.reply("Ping!");  // If it's pong then we ping
});

client.on("interactionCreateEvent", (in: Interaction) => {
  if(in.getCommand().name === "ping") in.reply("Pong!");      // If the content is ping then we pong
  else if(in.getCommand().name === "pong") in.reply("Ping!"); // If it's pong then we ping
});

client.authenticate();
```

The examples above are using TypeScript to give readers some contextual applications. The name shortening rule can be virtually applied to any applications regardless of programming languages.
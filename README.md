[![discordjs-pagination](https://user-images.githubusercontent.com/57099786/126899921-eb1e0728-ab64-4d28-a59c-835662957a8a.png)](https://npmjs.com/package/discordjs-button-pagination)

<div align="center">
  <p>
    <a href="https://www.npmjs.com/package/discordjs-button-pagination-v2/"><img src="https://nodei.co/npm/discordjs-button-pagination-v2.png?downloads=true&stars=true" alt="NPM info" /></a>
  </p>
</div>

# discordjs-button-pagination-v2
A simple package to paginate discord embeds via discord buttons introduced in [discord.js v13](https://github.com/discordjs/discord.js/tree/master).

# Versions

## `discordjs-button-pagination-v2@interaction` [Default]
for slash command interaction.

# Installation

### Default command: `npm install discordjs-button-pagination-v2`

# Requirements
Node.js 16.6.1 or newer is required along with Discord.js 13.0.0 or newer.


# Usage for Interaction (Slash Command)
__Basic Bot Example__
```js
// Import the discordjs-button-pagination package
const paginationEmbed = require('discordjs-button-pagination-v2');

// Use MessageEmbed to make pages
// Keep in mind that Embeds should't have their footers set since the pagination method sets page info there
const { EmbedBuilder , ButtonBuilder, ButtonStyle} = require('discord.js');
const embed1 = new EmbedBuilder()
                .setTitle('First Page')
                .setDescription('This is the first page');

const embed2 = new EmbedBuilder()
                .setTitle('Second Page')
                .setDescription('This is the second page');

const button1 = new ButtonBuilder()
                .setCustomId('previousbtn')
                .setLabel('Previous')
                .setStyle(ButtonStyle.Danger);

const button2 = new ButtonBuilder()
                .setCustomId('nextbtn')
                .setLabel('Next')
                .setStyle(ButtonStyle.Success);

// Create an array of embeds
pages = [
	embed1,
	embed2,
	//....
	//embedN
];

//create an array of buttons

buttonList = [
    button1,
    button2
]


// Call the paginationEmbed method, first three arguments are required
// timeout is the time till the reaction collectors are active, after this you can't change pages (in ms), defaults to 120000
paginationEmbed(interaction, pages, buttonList, timeout);
// There you go, now you have paged embeds
```

# Note
This will not work with buttons whose style is set as 'LINK' as they do not trigger an interaction event. The buttons will auto disable once the the collector ends after the timeout.
You must use the following custom ids for it to work. "previousbtn" and "nextbtn"
## The collector timer resets after receiving a button interaction.

# Preview

First Page

![pic1](https://user-images.githubusercontent.com/57099786/126900536-0daa030b-eaae-4a00-ad1c-912a2a5ca6af.PNG)



Second Page

![pic2](https://user-images.githubusercontent.com/57099786/126900544-96fd0163-26f8-44b4-b823-f84756ae0028.PNG)



Disabled Buttons after collector end

![pic3](https://user-images.githubusercontent.com/57099786/126900553-b9ab9cb7-1dfd-45ae-9e31-469b249f0c18.PNG)



### For any issues or suggestions, kindly open an issue/pull request on the [**GitHub Repository**](https://github.com/chillingcone426/discordjs-button-pagination)


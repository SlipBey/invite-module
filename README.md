[![github](https://img.shields.io/badge/Github%20-1d202b.svg?&style=for-the-badge&logo=github&logoColor=white)](https://github.com/SlipBey/invite-module)
[![supportServer](https://img.shields.io/badge/Discord%20-7289DA.svg?&style=for-the-badge&logo=discord&logoColor=white)](https://slip.slipyme.xyz/discord)
[![totalDownloads](https://img.shields.io/npm/dt/invite-module?color=CC3534&logo=npm&style=for-the-badge)](http://npmjs.com/invite-module)
[![weeklyDownloads](https://img.shields.io/npm/dw/invite-module?color=CC3534&logo=npm&style=for-the-badge)](http://npmjs.com/invite-module)
[![version](https://img.shields.io/npm/v/invite-module?color=red&label=Version&logo=npm&style=for-the-badge)](http://npmjs.com/invite-module)
[![stars](https://img.shields.io/github/stars/SlipBey/invite-module?color=yellow&logo=github&style=for-the-badge)](https://github.com/SlipBey/invite-module)
[![license](https://img.shields.io/github/license/SlipBey/invite-module?logo=github&style=for-the-badge)](https://github.com/SlipBey/invite-module)

## Invite Modle

Discord.JS v13 Modulue.

## Installation

    $ npm install invite-module

## Examples

##Paramaters:

`member, invite, inviter, guild`

`member -> invited user and returns as server member`
`invite -> invite code`
`inviter -> inviter and return as user`
`guild -> in member guild`

##Client and Intent:
<pre><code>
const { Discord, Client, Collection, Intents, Guild } = require('discord.js');
const client = new Client({ 
    intents: [Intents.FLAGS.GUILDS, Intents.FLAGS.GUILD_MESSAGES, Intents.FLAGS.GUILD_MEMBERS, Intents.FLAGS.GUILDS,
    Intents.FLAGS.GUILD_MESSAGE_REACTIONS, Intents.FLAGS.GUILD_PRESENCES, Intents.FLAGS.GUILD_VOICE_STATES, Intents.FLAGS.GUILD_INVITES] ,
    partials: ['MESSAGE', 'CHANNEL', 'REACTION', 'ROLE', "GUILD_MEMBER", "USER", "GUILD_INVITES", "MANAGE_GUILD"],
    });
//calling the module
const invite = require('invite-module');
invite.inviteCounter(client);
</pre></code>

`guildMemberAdd`, `memberJoin` event now.
`guildMemberRemove`, `memberLeave` event now.

##Use:
<pre><code>
client.on("memberJoin", async(member, invite, inviter, guild) => {

    console.log(`${member} joined the server, inviting by: **${inviter.username}**.`);
    
})
client.on("memberLeave", async(member, invite, inviter, guild) => {

    console.log(`${member.user.tag} left the server, was invited by: **${inviter}**.`);
    
})
</pre></code>
Or:
<pre><code>
client.on("memberJoin", async(member, invite, inviter, guild) => {

    guild.channels.cache.get('channel-id').send(`${member} joined the server, inviting by: **${inviter.username}**.`);
    
})
client.on("memberLeave", async(member, invite, inviter, guild) => {

    guild.channels.cache.get('channel-id').send(`${member.user.tag} left the server, was invited by: **${inviter}**.`);
    
})
</pre></code>

##Use of invitation code and guild:
<pre><code>
client.on("memberJoin", async(member, invite, inviter, guild) => {

    console.log(`Joined ${member}, "${guild}" server, using invite code: ${invite}. Invited by: **${inviter.username}**`);
    or
    guild.channels.cache.get('channel-id').send(`Joined ${member}, "${guild}" server, using invite code: ${invite}. Invited by: **${inviter.username}**`);
    
})
</pre></code>

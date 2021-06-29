# Node.js-Project-I-need-help-
Making a discord bot but has an error (syntax: unexpected end of input) and I need help

```const app = express()
const Database = require("@replit/database")
const db = new Database()
app.get("/", (req, res) => {
  res.send("hello world")
})

client.login(process.env.token)

app.listen(3000,() => {
  console.log("Project is ready!")
})

let Discord = require ("discord.js")
let client = new Discord.Client()

client.on("ready", () =>{
  client.user.setPresence({activity: {name: "being a discord bot", status: "any status"}})
})

client.on("guildMemberAdd", member => {
  if(member.guild.id === "850466744581488640"){
    client.channels.cache.get("850486786433745017").send(`Welcome ${member}!`)
  }
})

client.on("message", message =>{
if(message.content === "ping") {
  message.channel.send("pong")
}

if(message.content.startsWith(".mute")){
  if(!message.member.hasPermission("KICK_MEMBERS")) return
  message.channel.send("You don't have permission to mute.")
  let role = message.guild.roles.cache.find(role =>
  role.name === "muted")
  let member = message.mentions.members.first()
  let reason = message.content.split(" ").slice(2).join(" ")
  if(!reason) reason = "No reason specified"
  if(!role) return message.channel.send("This server doesn't have a muted role.")
  if(!member) return message.channel.send("You didn't mention a member.")
  if(member.role.cache.has(role.id)) return
  message.channel.send("That user is already muted.")
  member.roles.add(role)
  .then(() => {
    message.channel.send(`Successfully muted ${member} with reason: ${reason}`)
  })
   .catch(() => {
    message.channel.send("Oops, something went wrong.")
  })
}

if(message.content === ".nickname") {
  let nickname = ["smoothiepro", "smoothieisbest", "sub2smoothie", "SUBSKRAIB2SMOOTHIE"]
  message.channel.send(`${nickname[Math.floor(Math.random() * nickname.length)]} is your new name.`)
}
  if(message.content.startsWith(".kill")) {
    let victim = message.mentions.users.first()
    if(!victim) message.reply("Mention someone to kill")
    else{
      message.channel.send(`${victim} has died.`)
    }
  }
  if(message.content.startsWith(".kick")) {
    if(message.member.hasPermission("KICK_MEMBERS")) {
      let member = message.mentions.members.first()
      if(!member) message.channel.send("Please mention someone")
      else {
        member.kick().then(mem => {
          message.channel.send(`Kicked ${mem.user.username}!`)
        })
      }
    } else {
      message.reply("You don't have permission to do this.")
    }
  }
  if(message.content === ".catimage") {
    let image = new Discord.MessageAttachment("https://www.thesprucepets.com/thmb/gY_3zGT4Nasd_NM2QYu1iNj-6s8=/1080x721/filters:no_upscale():max_bytes(150000):strip_icc()/cutest-cats-on-the-internet-4-57eeab3c5f9b586c3549f9c2.jpeg")
    message.channel.send(image)
  }
  if(message.content === ".kill") {
    let image = new Discord.MessageAttachment("https://www.google.com/search?q=graveyard+image&rlz=1C1SQJL_enUS826US826&sxsrf=ALeKk00GgjhJrBi3DNyEiuOe6lPiNJ6shQ:1624900748804&tbm=isch&source=iu&ictx=1&fir=9gMtgtGTEFIbQM%252CwBDswrMZw51dVM%252C_&vet=1&usg=AI4_-kR8iHCeTiTdSa2r21Ptp8PF5jBwcA&sa=X&ved=2ahUKEwjdj7X_6rrxAhUBGFkFHXqtDhAQ9QF6BAgIEAE#imgrc=9gMtgtGTEFIbQM")
    message.channel.send(image)
  }
  if(message.content === ".rickroll") {
    let image = new Discord.MessageAttachment("https://media3.giphy.com/media/g7GKcSzwQfugw/200w.gif?cid=82a1493bx6tle1ut4bfnzw1zqgyjpw5vbw51c4j1fit3fbhu&rid=200w.gif&ct=g")
    message.channel.send(image)
    message.channel.send("You have Rick Rolled yourself. Try to be smarter next time.")
  }
  if(message.content === ".smoothie") {
  let embed = new Discord.MessageEmbed()
  .setTitle("why did you do this")
  .setDescription("the man who abuses a discord bot")
  .setFooter("if you found this dm me your cool")
}

  if(message.content.startsWith(".unmute")){
  if(!message.member.hasPermission("KICK_MEMBERS")) return
  message.channel.send("You don't have permission to mute.")
  let role = message.guild.roles.cache.find(role =>
  role.name === "muted")
  let member = message.mentions.members.first()
  let reason = message.content.split(" ").slice(2).join(" ")
  if(!reason) reason = "No reason specified"
  if(!role) return message.channel.send("This server doesn't have a muted role.")
  if(!member) return message.channel.send("You didn't mention a member.")
  if(!member.role.cache.has(role.id)) return
  message.channel.send("That user is not muted.")
  member.roles.remove(role)
  .then(() => {
    message.channel.send(`Successfully unmuted ${member} with reason: ${reason}`)
  })
   .catch(() => {
    message.channel.send("Oops, something went wrong.")
})

if(message.content.startsWith(".ban")) {
  if(message.member.hasPermission("BAN_MEMBERS")) {
    let member = message.mentions.members.first()
    if(!member) message.channel.send("Please mention someone")
    else {
      member.ban().then(mem => {
        message.channel.send(`Banned ${mem.user.username}!`)
      })
    }
  } else {
    message.reply("You don't have permission to do this.")
  }
}
if(message.content.startsWith(".snipe")) {
  let channel = message.mentions.channels.first() || message.channel
  let msg = client.snipe.get(channel.id)
  if(!msg) return message.channel.send("There is nothing to snipe.")
  let embed = new Discord.MessageEmbed()
  .setTitle(msg.author.tag)
  .setThumbnail(msg.author.displayAvatarURL({dynamic: true}))
  .setColor("RANDOM")
  .setDescription(msg.content)
  if(msg.attachments.first()) embed.setImage(msg.attachments.first().url)
  message.channel.send(embed)
}
client.snipe = new Discord.Collection()
client.on("messageDelete", deletedMsg => {
  client.snipe.set(deletedMsg.channel.id,deletedMsg)
})
client.on("message", message => {
  const args = message.content.split(" ").slice(1)
})

if(message.content.startsWith(".purge")) {
  if(!message.member.hasPermission("MANAGE_MEMBERS")) return
  message.channel.send("Missing Permission.")
  let amountToPurge = args [0]
  if(isNaN(amountToPurge)) return message.channel.send("Must provide an integer")
  message.delete()
  message.channel.bulkDelete(amountToPurge)
  message.channel.send(`Deleted ${amountToPurge} messages!`).then(v => v.delete({timeout: 5000}))
}
  
const topUsers = [];
if(message.content.startsWith(".cpstest")) {
client.on('message', (message) => {
  if (message.author.bot) return;

  let CPStest = new Discord.MessageEmbed()
    .setColor('#8f82ff')
    .setTitle('CPS Test')
    .setDescription(
      `Alright, ${message.author.username}. Ready to begin your CPS test? All you have to do is spam click this reaction above ^ as fast as you can, you have 10 seconds before the timer runs out. Good Luck!`,
    )
    .setFooter(
      'Note: This may be inaccurate depending on Discord API and Rate Limits.',
    );
  message.channel.send(CPStest);
  message.react('🖱️');

  // Create a reaction collector
  const filter = (reaction, user) =>
    reaction.emoji.name === '🖱️' && user.id === message.author.id;

  let clicks = 1 * 3; // (total clicks)
  const timespan = 10; // (time in seconds to run the CPS test)

  const collector = message.createReactionCollector(filter, {
    time: timespan * 1000,
  });

  collector.on('collect', (r) => {
    console.log(`Collected a click on ${r.emoji.name}`);
    clicks++;
  });

  collector.on('end', (collected) => {
    message.channel.send(
      `Collected ${clicks} raw clicks (adding reactions only)`,
    );
    clicks *= 2;
    message.channel.send(`Collected ${clicks} total approximate clicks.`).then(v => ({timeout: 5000}));

    const cps = clicks / timespan / 0.5;
    message.channel.send(
      `Your CPS averaged ~${cps} clicks per second over ${timespan} seconds.`,
    );

    topUsers.push({ tag: message.author, cps });

    let cpses = '';
    let usernames = '';
});
 
client.on("message", async message =>{
if(message.content === "ping") {
  message.channel.send("pong")
}

  if(message.content.toLowerCase().startsWith(".balance")) {
let balance = await db.get(`wallet_${message.author.id}`)
let bank = await db.get(`bank_${message.author.id}`)
}
if (balance === null) balance = 0
if (bank === null) bank = 0
message.channel.send(`Your wallet: ${balance} and your bank: ${bank}`)
    
if(message.content.toLowerCase().startsWith(".daily")) {
  const check = await db.get(`dailyCheck_${message.author.id}`);
  const timeout = 86400000
  if(check !== null && timeout - (Date.now() - check) > 0) {
    const ms = require("pretty_ms")
    const timeLeft = ms(timeout - (Date.now() - check ))
    message.channel.send(`Woah wait there speedy! You have already claimed your daily prize and still need to wait ${timeLeft}`)
  } else {
    let reward = 1000
    let currentBalance = await db.get(`wallet_${message.author.id}`)
    message.channel.send(`You have claimed ${reward.toLocaleString()}${currency} and come back tomorrow for another reward!`)
}
}})}})```

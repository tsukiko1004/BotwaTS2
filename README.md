package com.botwa;

public class bot {

  public static void main(String[] args) {

   

  }

}

GNU nano 5.4                                                            index.js

const  XBOT = 'Tsukiko'; // Nama Bot Whatsapp

const instagram = 'https://instagram.com/bluezone.nime'; // Nama Instagramlu cok                                                                     const nomer = 'https://Wa.me/+6281214995864'; // Nomor whatsapplu cok

const aktif = 'Tergantung kuota'; // Kapan bot lu aktif                                                                                                 const groupwa = 'comming soon'; // OFFICIAL GRUP LU 1                                                                                                   const youtube = 'https://youtube.com/channel/UCYKxsg7iF9a9IZyXQRNsvqw';

const qrcode = require("qrcode-terminal");                                                                                                              const moment = require("moment");

const cheerio = require("cheerio");                                                                                                                     const get = require('got')

const fs = require("fs");

const dl = require("./lib/downloadImage.js");

const fetch = require('node-fetch');

const urlencode = require("urlencode");

const axios = require("axios");

const imageToBase64 = require('image-to-base64');

const donate = require("./lib/donate.js");

const info = require("./lib/info.js");

const menu = require("./lib/menu.js");

const speed = require('performance-now');

const readTextInImage = require('./lib/ocr')

const vcard = 'BEGIN:VCARD\n' // metadata of the contact card

            + 'VERSION:3.0\n'

            + 'FN:affis\n' // full name

            + 'ORG:Owner  XBOT Bot;\n' // the organization of the contact

            + 'TEL;type=CELL;type=VOICE;waid=6282334297175:+62 823-3429-7175\n' // WhatsApp ID + phone number

            + 'END:VCARD'

const

{

   WAConnection,

   MessageType,

   Presence,

   MessageOptions,

   Mimetype,

   WALocationMessage,

   WA_MESSAGE_STUB_TYPES,

   ReconnectMode,

   ProxyAgent,

   waChatKey,

   GroupSettingChange,

   mentionedJid,

   processTime,

} = require("@adiwajshing/baileys");

var jam = moment().format("HH:mm");

function foreach(arr, func)

{

   for (var i in arr)

   {

      func(i, arr[i]);

   }

}

const conn = new WAConnection()

conn.on('qr', qr =>

{

   qrcode.generate(qr,

   {

      small: true

   });

   console.log(`[ ${moment().format("HH:mm:ss")} ] XBOT Ready scan now!`);

});

conn.on('credentials-updated', () =>

{

   // save credentials whenever updated

   console.log(`credentials updated$`)

   const authInfo = conn.base64EncodedAuthInfo() // get all the auth info we need to restore this session

   fs.writeFileSync('./session.json', JSON.stringify(authInfo, null, '\t')) // save this info to a file

})

fs.existsSync('./session.json') && conn.loadAuthInfo('./session.json')

// uncomment the following line to proxy the connection; some random proxy I got off of: https://proxyscrape.com/free-proxy-list

//conn.connectOptions.agent = ProxyAgent ('http://1.0.180.120:8080')

conn.connect();

conn.on('user-presence-update', json => console.log(`[ ${moment().format("HH:mm:ss")} ] => bot by @affis_saputro123`))

conn.on('message-status-update', json =>

{

   const participant = json.participant ? ' (' + json.participant + ')' : '' // participant exists when the message is from a group

   console.log(`[ ${moment().format("HH:mm:ss")} ] => bot by @affis_saputro123`)

})

conn.on('message-new', async(m) =>

{

   const messageContent = m.message

   const text = m.message.conversation

   let id = m.key.remoteJid

   const messageType = Object.keys(messageContent)[0] // message will always contain one key signifying what kind of message

   let imageMessage = m.message.imageMessage;

   console.log(`[ ${moment().format("HH:mm:ss")} ] => Nomor: [ ${id.split("@s.whatsapp.net")[0]} ] => ${text}`);

   // Groups

if (text.includes("#buatgrup"))

   {

var nama = text.split("#buatgrup")[1].split("-nomor")[0];

var nom = text.split("-nomor")[1];

var numArray = nom.split(",");

for ( var i = 0; i < numArray.length; i++ ) {

    numArray[i] = numArray[i] +"@s.whatsapp.net";

}

var str = numArray.join("");

console.log(str)

const group = await conn.groupCreate (nama, str)

console.log ("created group with id: " + group.gid)

conn.sendMessage(group.gid, "hello everyone", MessageType.extendedText) // say hello to everyone on the group

}

if(text.includes("#cek")){

var num = text.replace(/#cek/ , "")

var idn = num.replace("0","+62");

console.log(id);

const gg = idn+'@s.whatsapp.net'

const exists = await conn.isOnWhatsApp (gg)

console.log(exists);

conn.sendMessage(id ,`${gg} ${exists ? " exists " : " does not exist"} on WhatsApp`, MessageType.text)

}

else if (text == 'assalamualaikum'){

conn.sendMessage(id, '3aalaikumsalam, Ketik #menu/#info/#donasi Contoh #menu' ,MessageType.text);

}

else if (text == 'salam'){

conn.sendMessage(id, 'Waalaikumsalam, Ketik #menu/#info/#donasi Contoh #menu' ,MessageType.text);

}

else if (text == 'asalamualaikum'){

conn.sendMessage(id, 'Waalaikumsalam, Ketik #menu/#info/#donasi Contoh #menu' ,MessageType.text);

}

else if (text == 'Assalamualaikum'){

conn.sendMessage(id, 'Waalaikumsalam, Ketik #menu/#info/#donasi Contoh #menu' ,MessageType.text);

}

else if (text == 'p'){

conn.sendMessage(id, 'Ya?, Ketik #menu/#info/#donasi Contoh #menu' ,MessageType.text);

}

else if (text == 'P'){

conn.sendMessage(id, 'Ya?, Ketik #menu/#info/#donasi Contoh #menu' ,MessageType.text);

}

else if (text == 'Halo'){

conn.sendMessage(id, 'Ya?, Ketik #menu/#info/#donasi Contoh #menu' ,MessageType.text);

}

else if (text == 'Asu'){

conn.sendMessage(id, 'Lu Asw' ,MessageType.text);

}

else if (text == '#owner'){

conn.sendMessage(id, 'Owner XBOT wa.me/+62812 1499 5864' ,MessageType.text);

}

else if (text == 'affis'){

conn.sendMessage(id, 'Aku BOT nya XBOT' ,MessageType.text);

}

else if (text == 'audio'){

conn.sendMessage(id, 'pacar owner ihh' ,MessageType.text);</s> </s> </s> </s> </s> </s> </s> </s> </s> </s> </s> </s> </s> </s> </s> </s> </s> </s> </s> </s> </s> </s> </s> </s> </s> </s> orang </s>

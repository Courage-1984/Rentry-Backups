# Slav Art Beginner Information
This is a brief overview of some important information that will help you with using our music bots.
## Table of contents:
- [Choosing download quality](https://rentry.org/slavart#choosing-download-quality)
- [Getting a proper artist & playlist URL from Qobuz](https://rentry.org/slavart#getting-a-proper-artist-playlist-url-from-qobuz)
- [Zip file only contains album cover?](https://rentry.org/slavart#zip-file-only-contains-album-cover)
- [Additional information](https://rentry.org/slavart#additional-information)

### Choosing download quality
ID | Quality
-| -
0 | 128 kbps MP3 or AAC
1 | 320 kbps MP3 or AAC
2 | 16 bit, 44.1 kHz (CD)
3 | 24 bit, ≤ 96 kHz
4 |  24 bit, ≤ 192 kHz

To choose a different quality, simply add the quality ID behind your dl command like so:
`!dl <url> <quality id>`
**Example: ** `!dl https://www.deezer.com/en/album/305629827 3`

The quality argument is **completely optional**, you do not need to specify the quality every time, **it will default to the highest available quality.**
Keep in mind this **only** works for Deezer, Qobuz and Tidal (Soundcloud, Apple and Spotify don't support this. They are limited to max 256kbps M4A and 320kbps OGG respectively)

### Getting a proper artist & playlist URL from Qobuz
Downloading Qobuz artist profiles requires a URL that contains their artist ID. The normal artist links will not work.

How to get that url without an account:
1. Go to the artist profile, right click the button that says "Listen on Qobuz" and copy the link
2. The link will look like this: `qobuzapp://artist/<id>`   Copy that id
3. Your link should now look like this:  `https://play.qobuz.com/artist/<id>`
**Example**: https://play.qobuz.com/artist/5243973

** OR **

You can use this User Script that let's you easily copy the artist link for Slav Art.
First you are going to need ViolentMonkey for your web browser, you can get it here: [https://violentmonkey.github.io](https://violentmonkey.github.io/get-it/).
Once you have it installed click on [this](https://gist.github.com/crackhub-dev/cce7799296a9b34eec94d74247b8fc1e/raw/19b2b0aaa2767330c33390a33f67825dfcd74083/qobuz_artist_slavart.user.js) link and hit "Confirm installation".
Now if you visit a www.qobuz.com artist page, you should find a new button that reads "Copy Slav Art link", it will copy the proper URL to your clipboard!

Same goes for playlists
instead of `https://www.qobuz.com/us-en/playlists/<id>` use `https://play.qobuz.com/playlist/<id>`
**Example**: https://play.qobuz.com/playlist/892501 


### Zip file only contains album cover?
If the zip file you got from one of the bots only contains the album cover instead of the music files, that means the album you tried to download was blocked in the region of our account for that streaming service. 
**Our account regions are currently:**
Deezer: us (USA)
Qobuz: 🇺🇸 (USA)
Spotify: au (AUSTRALIA)
Tidal: 🇺🇸 (USA)
Apple: 🇺🇸 (USA)
If you face the issue mentioned above (or other geo-related errors), use our extra qobuz channels regions (in discord) or try requesting an upload of the album you want in #request channel maybe someone in the community has access to an account in a region where it's not blocked.


### Additional information
**Q: How to download entire artist profiles and playlists?**
A: You can download entire artist profiles and playlists in Artist-Playlist channels only
**Q: How to transfer playlists from/to TIDAL, Apple Music, YouTube, Amazon Music, Pandora and many more?**
A: [This site](https://www.tunemymusic.com/) can help you achieve that.
**iOS siri shortcut for slavart.gamesdrive.net**
Created by HenryThe6th#2791
https://www.icloud.com/shortcuts/17bb268f2d4f484e85f9cc07fcecbb1f

### More information's provided by florinsdistortedvision#3041
This is a brief overview of some important information that will help you with using our music bots.

## How to use the bots?

### Request via the bot
- Bot will react and grab your requests **only if** sent a correct command + correctly formatted album/song link in Main Bot section (#music-dl-request),  Artist Playlist~ section or either of Qobuz UK/NZ~ section
==~ - only found on Slav's Discord.==
- The correct command is the [channel's prefix](https://imgur.com/a/UbCZmsE) followed by dl and correct link.
Example: `!dl https://www.deezer.com/en/album/71652`
- For music links, **do not use the app's share function as the bot will likely not work for most services!** Correct link format (copy URL from a browser) to get your links **(remove any additional junk if link has more characters)**:
	- For Qobuz: https://www.qobuz.com/us-en/album/albumname/xxxxxxx
*(play.qobuz.com links are also supported)*
✅ Example of correct link: `https://www.qobuz.com/us-en/album/wu-tang-forever-wu-tang-clan/5099749766921` or `https://play.qobuz.com/album/5099749766921`
‎
‎
	- For Deezer: https://www.deezer.com/en/album/xxxxxx (/en/ is just the page's language not region here!)
✅ Example of correct link: `https://www.deezer.com/en/album/71652  `
❌ Example of incorrect link (extra junk after track ID): `https://www.deezer.com/en/track/1046912962?deferredFl=1&utm_campaign=track&utm_source=google&utm_medium=organic`
❌ Example of incorrect link (app's share URL): `ttps://deezer.page.link/uSbwQm2FGKcYwHT86`
‎
‎
	- For Tidal: https://listen.tidal.com/ or https://tidal.com/browse/album/xxxxx **(for second link, a lot of removed albums/songs are still showed, so its best to search via the first link).**
✅ Example of correct link: `https://listen.tidal.com/album/1632623` or `https://tidal.com/browse/album/19193427` (if second doesn't work, check below on fixing the bot's error)
‎
‎
	- For Youtube Music:  https://music.youtube.com/watch?v=xxxxxxx
✅ Example of correct link: `https://music.youtube.com/playlist?list=OLAK5uy_nAoxWhmErTOTms5o_LsORfKWls4A2tQ5k`
❌ Example of incorrect link (this is a regular Youtube link, NOT Youtube Music): `https://www.youtube.com/playlist?list=OLAK5uy_nAoxWhmErTOTms5o_LsORfKWls4A2tQ5k`
‎
‎
	- For Soundcloud: https://soundcloud.com/artist/song (**sets -playlists and albums-, artist discographies are NOT supported**)
✅ Example of correct link: `https://soundcloud.com/stanlepard/windows-98-velkommen`
❌ Example of incorrect link (extra junk from app's share URL) : `https://soundcloud.com/stanlepard/windows-98-velkommen?si=be2ae10f19824e729c9601714398f797&utm_source=clipboard&utm_medium=text&utm_campaign=social_sharing`
‎
‎
	- For Apple: https://music.apple.com/us/album/your-song-name/xxxxxxxxx
✅ Example of correct link: `https://music.apple.com/us/album/wu-tang-forever/268503472` (beta.music.apple.com links also work)
‎
‎
	- For Spotify: https://open.spotify.com/album/xxxxxxxxxx or https://open.spotify.com/track/xxxxxx?si=xxx (for tracks)
✅ Example of correct link: `https://open.spotify.com/album/4r3TaXjF2b1qwCpxjIpW43`
❌ Example of incorrect link : `spotify://2914010400`This is a brief overview of some important information that will help you with using our music bots.

### Understanding and fixing bot errors

1) `Error: Couldn't rip linkurl (Most likely: GEO restriction.) ` or  `Error: Couldn't rip linkurl (possible reasons: region restrictions?, invalid link?, purchase only?) `
- These are the most common errors you will see. Errors can mean either:
	- Your link is incorrect (See above how links should look)
	- Your request can not be streamed from bot's region (Use extra qobuz region channels ro #request)
	- Your request is not streamable anymore (removed from the service)
	- In case of Qobuz and Apple, your request is only available for purchasing but not streaming (bot cannot buy it for you!). **[See this for how to identify such cases](https://imgur.com/a/id0Fvi6)**
	- **A VPN will NOT fix the error, as regions are dictated by the bot's account region!**

2) `Downloading artists and playlists is not allowed!`
- Pretty self explanatory, please take another look at how links should look
- **Only use Artist-Playlist channel for requesting artist discographies and playlists!**

3) `Invalid service. Valid services: tidal, qobuz, deezer, soundcloud, spotify, music.apple`
- As the info says, your request cannot be completed because the bot has no support for your link. As a alternative, try to request to people who may have it in #request channel.

## Server channel information

- Main server section
	- announcement - Updates and news about Slav services, additions and removal of services
	- status - News about bot, list of enabled services and maximum quality for each service
	- faq - Place for the clueless to get enlightened :)
	- account-providers - A list of account providers for the bot. Without them the bot would be useless. Thank them!

- Bot section
	- Main Bot section - (request to send links, uploads where the bot finishes your request).
	- Main Bot Zippyshare~ - used when qouta error or alternative to Main Bot
	- Artist-Playlist~ - channel meant for requesting artist discographies and playlists
	- Qobuz UK and Qobuz NZ~ - channel meant for requests only found in United Kingdom and New Zealand (region-locked).
==~ - Only on Discord==

- Chat section
	- general - general talk about anything
	- request - channel for requesting from people a particular album/song etc if the bot can't get it. **This is NOT a bot channel and people that may help are NOT bots!**
	- community-uploads - channel to upload to everyone a particular album/song that is not requested. Sharing is caring. **Any talk that's not links will get removed ! If you have a question, go to general and tag the uploader!**
	- show-n-tell - channel to flex on anything flexable.
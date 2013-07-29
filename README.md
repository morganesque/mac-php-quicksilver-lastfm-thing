A Mac PHP Quicksilver Last.fm thing
===================================

I made this because I have Spotify on the living room laptop playing me music but I sit working in the dinning room (on the big table) and sometimes I just wonder what the current song is. Obviously I don't want to get up and walk over. Christ! I don't even walk to reach for the mouse.

So, because I scrobble the Spotify up to Last.fm (which generally is pretty quick) I realised that I could just ask Last.fm to tell me what it is. This was simpler than attempting to get into some Spotify API (is there one?) and because the Last.fm API is public (at least for this info) it was simple to grab it.

## Quicksilver ##
So I'm using Quicksilver to trigger it. I just want to be able to bring up Quicksilver, run the command and see the title, artist and maybe the album just come up in front of me. Quicksilver's Large Type function is really nice for this if you can just pipe the right content into it.

## AppleScript ##

I found that I needed to create a little AppleScript which Quicksilver can then call. This was because I wanted to pass the content I'd found back into Quicksilver's large text input which I don't think I could have done by simply calling the PHP script directly. You need to make sure the AppleScript you create is something Quicksilver can find. You can do this directly in the Quicksilver prefs, or just stick the AppleScript in a folder Quicksilver is already scanning.

```
tell application "Quicksilver"
    activate
    set s to do shell script "~/bin/lastfm"
    show large type s
end tell
```

## PHP ##
PHP does the "heavy" lifting, grabbing JSON from Last.fm and digging through it to find what I'm after. Then it just takes the right bits and formats them nicely for Quicksilver. If you want to use it you'll have to get a Last.fm API key from the website and obviously you'll probably want to change the Last.fm username to yours (unless you're stalking me in which case you're good to go).
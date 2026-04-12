# URL Formats
- `amagi.tv` and `telvue.com` links do not need any values after `playlist.m3u8` in the URL
- `video.tegnaone.com` needs only the `ads.content_ID=` value after `index.m3u8?`

# Obfuscation Techniques
- `doubleclick.net` links are usually hiding a `dai.google.com` link behind them

# Observed-Problems
*Fastly provides content delivery network services*
- `fastly.net` links require a valid token and expiry epoch date string

*"Disney Streaming Services" backended by Akamai CDN, requires a widevine decryptor*
- `dssott.com` :: requires multiple variables in the URL for widevine decryption

*"Google Dynamic Ad Insertion (DIA)" stitches ads directly into live or on-demand content*
- `dai.google.com` :: variable between `stream/` and `/master.m3u8` appears to be some kind of time-gated token

# Observed Variable Requirements
*No easily accessible documentation found for `lura.live`*
- `lura.live` :: two values are required after `rendition.m3u8` for the stream to function
   - `track=` specifies the video stream or rendition to be played when multiple variants exist in the manifest
   - `anvsid=` is the "Anvato Session ID"  that acts as a unique token for the specific viewing session

*Syncbak, Inc. is a media technology company that powers live streaming, OTT, and ad insertion for broadcasters. They operate "SimpleSync" (live-stream transcoding) and launched the "Zeam" app for local TV streaming.*
- `aws.syncbak.com` :: two alues are required after `media.3mu8` for the stream to function
   - `bitrate=` defines the quality level of the video being served (adaptive bitrate streaming)
   - `session=` token associated with an x-atv-session-id HTTP header, used to identify a specific viewing session / track ad exposure / monitor performance on smart TVs
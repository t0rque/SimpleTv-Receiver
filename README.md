# SimpleTv Cast Receiver

Custom Chromecast receiver for SimpleTv IPTV app.

## 🎯 What is This?

This is a custom Google Cast receiver that handles HTTP 302 redirects for IPTV streams with tokenized URLs.

## 🚀 Live Receiver

**URL**: https://t0rque.github.io/SimpleTv-Receiver/

Use this URL when registering your Cast application in the [Google Cast Console](https://cast.google.com/publish).

## 🔧 How It Works

1. **Intercepts Load Requests**: When SimpleTv app casts media, this receiver intercepts the load request
2. **Follows Redirects**: Uses browser's Fetch API to follow HTTP 302 redirects
3. **Resolves Tokens**: Gets the final tokenized streaming URL
4. **Plays Media**: Streams the resolved URL on Chromecast

### The Problem It Solves

IPTV providers often use HTTP redirects for authentication:

```
Original URL:  http://provider.com/live/user/pass/channel.m3u8
              ↓ (302 Redirect)
Final URL:     http://cdn.com/live/play/[TOKEN]/channel
```

The Default Media Receiver can't follow these redirects, causing **Error 2103 (INVALID_REQUEST)**. This custom receiver solves that!

## 📊 Technical Details

- **Framework**: Google Cast Application Framework (CAF) v3
- **Supported Formats**: HLS (.m3u8), MPEG-DASH, MP4
- **Redirect Handling**: Automatic via Fetch API
- **Logging**: Debug logs available via Chrome Remote Debugging

## 🔍 Debugging

To view receiver logs:

1. Open Chrome on your computer
2. Go to `chrome://inspect/#devices`
3. Find your Chromecast under "Cast"
4. Click "inspect"
5. Check Console tab for logs

Expected logs:
```
[SimpleTv] 📡 Load request received
[SimpleTv] 📺 Original URL: http://...
[SimpleTv] ✅ Resolved URL: http://...
[SimpleTv] ▶️ Playback started
```

## 📱 Related Projects

- **SimpleTv App**: Main IPTV application (private repo)
- **Receiver**: This repository (public for Cast hosting)

## 📜 License

MIT License - Free to use and modify

## 🤝 Contributing

This is a simple receiver with minimal code. If you find bugs or improvements:

1. Fork this repo
2. Make your changes
3. Submit a pull request

## 💡 For Developers

Want to use this receiver for your own IPTV app?

1. Fork this repo
2. Deploy to your own GitHub Pages
3. Register in Cast Console with your URL
4. Update `receiverAppId` in your app

That's it! Free custom receiver for handling IPTV redirects.

## 🌟 Credits

Built for SimpleTv - Simple, fast IPTV streaming on Android.

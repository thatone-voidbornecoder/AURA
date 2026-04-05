# aura

**A 3D low-poly ambient music visualizer that reacts to what you're actually listening to.**

Connect Spotify and watch your room shift — lighting, weather, the cat's mood, even the wall colour — all driven live by the energy and palette of whatever's playing.

[**Live demo →**](https://aura-rouge-omega.vercel.app)

---

## what it does

- **3D isometric room** built in Three.js with real-time dynamic lighting
- **Spotify integration** via PKCE OAuth — no backend needed, runs fully client-side
- Room colour palette extracted directly from the **album art** of the current track
- Mood + energy from Spotify's **audio features API** drives the atmosphere
- **Weather through the window** reacts to track mood — rain, stars, or clouds
- **Cat in a bed** near the TV — sleeps on chill tracks, perks up on high energy ones
- **Mug steam** speed varies with energy
- **4 camera angles** with smooth cinematic transitions and subtle drift
- **Time of day toggle** — day / dusk / night changes window light and sky

### clickable room objects

| Object | Action |
|---|---|
| Floor lamp | Toggle on / off |
| Side table lamp | Toggle on / off |
| Candle | Snuff / relight |
| TV screen | Toggle display on / off |
| TV console | Cycle visualizer — bars → spectrogram → off |
| Vinyl player | Play / pause |
| Mug | ☕ |

---

## setup

### 1. get a Spotify Client ID

1. Go to [developer.spotify.com/dashboard](https://developer.spotify.com/dashboard)
2. Create a new app — name it anything, set type to **Web**
3. Under **Redirect URIs**, add your deployed URL exactly as it appears in the browser, e.g. `https://aura-rouge-omega.vercel.app`
4. Copy your **Client ID**

### 2. add your Client ID to the code

Open `index.html` and find this line near the top of the script:

```js
var SPOTIFY_CLIENT_ID = 'YOUR_CLIENT_ID_HERE';
```

Replace `YOUR_CLIENT_ID_HERE` with your actual Client ID.

> There are no environment variables or build steps — this is a single HTML file with no dependencies beyond Three.js loaded from CDN.

### 3. deploy

Push `index.html` and `vercel.json` to your repo. Vercel will auto-deploy on every push to `main`.

The `vercel.json` handles routing so the OAuth redirect back to `/` works correctly.

---

## local development

Just open `index.html` directly in a browser. Spotify OAuth won't work locally over `file://` (it requires https), but the room itself loads fine so you can work on visuals without connecting.

For OAuth testing locally, use a tool like [live-server](https://www.npmjs.com/package/live-server) or VS Code's Live Server extension and add `http://localhost:PORT` as an additional redirect URI in your Spotify app dashboard.

---

## file structure

```
AURA/
├── index.html      # entire app — single file, no build step
└── vercel.json     # routing config for Vercel
```

---

## tech

- [Three.js r128](https://threejs.org/) — 3D rendering
- Spotify Web API — currently playing, audio features
- PKCE OAuth — client-side auth, no backend
- Vanilla HTML / CSS / JS — no frameworks, no bundler

---

## roadmap

- [ ] Sidebar for room customisation (Sims-style furniture placement)
- [ ] Multiple scene types beyond the cozy room
- [ ] Apple Music + YouTube Music support
- [ ] Room preset marketplace — share your setup
- [ ] Mobile touch support

---

*built by [@thatone-voidbornecoder](https://github.com/thatone-voidbornecoder)*

# hua-kya — shift out-time counter

Office wants exactly **9h 30m** door-to-door. One minute short = half-day salary cut.
Punch in your arrival time once; it shows the exact safe out-time, a live countdown,
and alerts you 15 minutes before and at the deadline.

Pure static — `index.html` + `manifest.json`, no backend.

```sh
python3 -m http.server 8000
```

Open `http://<your-laptop-ip>:8000` on your phone → share menu → **Add to Home Screen**.

## Deploy (Render free tier)

Push to GitHub → Render → **New → Static Site** → pick the repo. `render.yaml` sets it up
(publish dir `.`, no build command). Free static sites don't spin down and come with
`https://`, so notifications work on the phone.

- **Buffer** (default +2 min) pads for clock drift between your phone, the biometric
  reader, and the walk to the gate. Tune it with the −/+ buttons.
- Alerts need the tab open; phones freeze background timers.
- System notifications require `https://` or `localhost` — over plain http on the LAN you
  still get the beep, the on-screen banner, and the countdown in the tab title. The Render
  URL is https, so notifications work there.
- `http://localhost:8000/?test=1` runs the time-math asserts; check the browser console.

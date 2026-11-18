# Zeekret

An Android phone + Wear OS watch app for the **Zeekr 7X**. Its main job is a reliable **Bluetooth digital
key**: the car unlocks as you walk up and locks as you walk away — once per arrival, predictable, no phone
tapping. Around that it adds remote control, trip and charging stats, automations, a home-screen widget and
push notifications. Inspired by, and built on, the open-source **OpenZeekr** project.
Not affiliated with Zeekr, Geely or ECARX.

**⬇ Download:** [latest release](https://github.com/pt-atlas/zeekret-updates/releases/latest) →
`Zeekret.N.apk` (phone) and `Zeekret-Watch.N.apk` (Wear OS watch). Open the APK on your phone and allow
"install unknown apps". New versions install over old ones. The app tells you when a newer version is out.

> 🚗 **Tested with the Zeekr 7X only (SEA region).** Using it with a 7X is **at your own risk**; using it
> with **any other Zeekr model is entirely at your own risk** — features may not work, may work differently,
> or may behave unexpectedly.

> 🧪 **Free, personal project — use at your own risk.** No warranty, no guarantee, no support. It may contain
> mistakes, and its developer accepts **no responsibility** for anything that happens from using it — a door
> that doesn't open or lock, a key that stops working, an account that gets signed out, or any other problem
> with your car, phone or account.

> ⚠️ **Your own car only.** Use Zeekret only with a Zeekr account and car that **you own or are explicitly
> allowed to use**.

> 🔒 **A Zeekr owner's private project, on a private server. No personal data is collected** — no location, no
> account, no driving data, no analytics. Your Zeekr account and keys stay on your phone (encrypted) and the app talks to the Zeekr
> cloud directly. The only link to our server is a code: the app's licence code, and for battery at arrival the car's
> pair code — and what travels with that code is locked so the server can't read it.

## The Zeekret apps

| App | Runs on | What it does |
|---|---|---|
| **Zeekret** (this one) | Phone + Wear OS watch | Bluetooth digital key, remote control, stats, widget, automations |
| **[Zeekret Dash](https://github.com/pt-atlas/zeekret-dash)** | Car head unit | Blindspot camera on the HUD, digital mirror, dash cam, car controls, automations, **battery at arrival** |
| **[Zeekret Maps Link](https://github.com/pt-atlas/zeekret-maps-link)** | Phone | Sends your live Google Maps route to Zeekret Dash, so the car shows the battery % you'll arrive with |

All three are free to try, closed-source, and published here as documentation and downloads only.

This repository holds **no source code** — only the releases and `latest.json`, the small file the app reads
to know whether a newer version exists.

## How Zeekret differs from the official app

1. **Digital key works on any Bluetooth-LE Android phone** — no approved-model list.
2. **Proximity unlock *and* walk-away lock — without DK 3.0.** Runs on the standard digital-key Bluetooth
   session; no DK 3.0 / UWB hardware needed. Tuned on real walk-up logs from a Zeekr 7X.
3. **Seat ventilation (cooling), not just heating** — on cars that have it.
4. **Standalone Wear OS companion** — lock / unlock directly over Bluetooth from the wrist.
5. **Automations and an instant widget** — auto-Sentry, auto-cool, auto-lock, left-open alerts; the widget's
   lock state flips the moment the car locks or unlocks.

## 🖥️ Head-unit side app: Zeekret Dash (experimental)

**Zeekret Dash** runs **on the Zeekr 7X head unit**, not on your phone. It's the next version of Blindspot, with car controls and automations added.

📖 **Full feature guide and changelog:** [pt-atlas/zeekret-dash](https://github.com/pt-atlas/zeekret-dash)

> 📲 **Install it from the car:** open the browser **on the car's head-unit screen**, go to
> **[zeekret.pages.dev](https://zeekret.pages.dev/)**, then download and install the app there.
> Opening the link on a phone or computer won't install it on the car.

**Home.** A grid of cards: tap one to act, hold it to open its settings. Car cards cover acceleration mode, steering,
damping (Performance trim only), the sunroof shade and the rear fog light.

**Blindspot.**
- When you indicate, that side's camera shows on the head unit, the HUD or both. It slides in and out in 0.2 s.
- The car's blindspot lamp (the light in the door mirror) gives that side's picture a red edge. Above 60 km/h it also
  opens the camera when you haven't indicated.
- It also opens on a door opening, a proximity warning, a forgotten indicator, or a turn without indicating (below 30 km/h).
- **Head-unit mirror:** Rearview, Slide-in or Blindspot view, with night anti-glare (Off / Low / High).

**Dash cam.** It records 1-minute clips at 2560×1440 to the USB stick, stamped with date, time, speed and position.
There's a Playback tab.

**Car controls.**

| Control | Choices |
|---|---|
| Acceleration mode | Comfort / Normal / Sport |
| Steering | Comfort / Standard / Sport |
| Damping | Comfort / Standard / Sport — **Performance trim only** (shows only when the app detects the car's damping value) |
| Sunroof shade | Closed / 25 / 50 / 75 % / Open |
| Rear fog light | On / Off |
| AC, temperature zones, tailgate height | on the Car page |

To find a car setting, take a snapshot, change the setting in the car's menu, then compare to see which signal
changed. **Search car signals** lists signals by name. Both only read from the car.

**Automations: "When … only if … do …"**
- **When:** the car turns on or off; the gear goes to P, D or R; speed reaches or drops to a value, or enters or
  leaves a range (0–200 km/h, in 5 km/h steps); outside temperature rises or drops to a value; it gets dark or
  light; rain starts or stops.
- **Only if:** workdays or weekend, gear, dark or light, raining or dry, speed above, below or between, outside
  temperature above or below.
- **Do:** any car control, plus app actions (Blindspot on/off, mirror, anti-glare, night dimming, dash cam).
- **No flickering:** a rule only fires again after the speed or temperature has moved back past its number, and at
  most once every 30 s for speed (60 s for temperature).

**Battery at arrival.** The car shows the battery % you'll arrive with, as one small line: **🔋 69% 🏁** (or
**🔋 62% 🏠** for home); orange below 20 %, red below 5 %. The destination comes from:
- **[Zeekret Maps Link](https://github.com/pt-atlas/zeekret-maps-link)** on your phone: the **live Google Maps
  route** (also through Android Auto). Change the destination in Google Maps and the car follows.
- **Zeekret (this app, .60 and newer):** in Google Maps tap a place ▸ **Share ▸ Zeekret ▸ Battery at arrival**. It
  also sends the car's average consumption from the Zeekr cloud, which makes the % more accurate.
- **Home** or a **saved place**, picked on the car.

Settings are under **Map link** in Zeekret Dash's side menu. Type the car's pair code (shown there) into Zeekret
(Settings) and / or Zeekret Maps Link. Everything sent is end-to-end encrypted; the server in between can't read it.

**About.** Settings backup saves all settings and rules to the USB stick and restores them (the licence isn't
included). The fault log can be sent to the developer for checking.

**Licence.** A 7-day free trial, then a paid licence (see the site). Your licence is kept when you update.

**Being worked on.** Finding the adaptive matrix high-beam signal, and smoother HUD video in town.

## Regions

| Region | Status |
|---|---|
| **SEA** | ✅ **Verified on a Zeekr 7X** |
| EU | From the original OpenZeekr code; not tested with Zeekret |
| LA / ME | Untested |

## 🔑 Getting your own keys (required)

To talk to the Zeekr cloud you supply **six keys** yourself, extracted from **your own** Zeekr app install:

- **Static, per-region keys** — `hmac_access_key`, `hmac_secret_key`, `password_public_key`: extract them from
  the Zeekr APK with **[Wysie/zeekr_key_extractor](https://github.com/Wysie/zeekr_key_extractor)**
  (`--region SEA` / `EU` / `LA`).
- **Runtime keys** — `prod_secret`, `vin_key`, `vin_iv`: read them from **your own** running Zeekr app with a
  dynamic-instrumentation tool (e.g. Frida), by observing `javax.crypto.Mac` / `SecretKeySpec` /
  `IvParameterSpec`. See the credited projects for the current recipe.

Enter them in the app's **first-run setup**, in **Settings**, or with **Import JSON**:

```jsonc
{ "hmac_access_key":"", "hmac_secret_key":"", "password_public_key":"",
  "prod_secret":"", "vin_key":"", "vin_iv":"",
  "email":"", "password":"", "vin":"" }
```

They're stored on your phone only, in encrypted storage.

## Proximity unlock / walk-away lock

Fixed signal levels, chosen in **Settings › Key setup** (tuned on a Zeekr 7X):

| Preset | Approach unlock | Walk-away lock |
|---|---|---|
| Closest | −68 dBm · ~2.3 m | below −80 dBm for 3 s · ~7 m |
| **Close** (recommended) | **−73 dBm · ~3.6 m** | below −84 dBm for 3 s · ~10 m |
| Far | −78 dBm · ~5.8 m | below −88 dBm for 3 s · ~14 m |

- Unlocks **once per arrival** (2 readings in a row at the unlock level); never repeat-unlocks.
- Walk-away lock only after you've been at the car, then a **20 s grace**, then below the lock level for 3 s —
  so it doesn't lock on you at the trunk.
- The car stops broadcasting its key ~7–13 min after it locks; on a walk-back, touch the handle to wake it.
- The Zeekr cloud allows one signed-in app per account — signing in here signs the official app out.

## Licence

Free. The app checks in with a licence server on start and every 12 h; each phone has a code in
**Settings › About › Licence**. A licence can be revoked in case of misuse, which stops the app on that phone.

## Credits & thanks 🙏

- **OpenZeekr** — the inspiration and groundwork Zeekret is built on.
- **[Wysie/zeekr_key_extractor](https://github.com/Wysie/zeekr_key_extractor)** — extracting the per-region app keys.
- **[Fryyyyy/zeekr_homeassistant](https://github.com/Fryyyyy/zeekr_homeassistant)** — the login / HMAC / vehicle-list cloud flow.
- **[mescon/zeekr-7x-home-assistant](https://github.com/mescon/zeekr-7x-home-assistant)** — the 3.0.x EU signing recipe and the runtime-key insight.
- Map data © OpenStreetMap contributors · weather data by Open-Meteo.com.

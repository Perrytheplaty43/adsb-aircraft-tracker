# ADS-B Aircraft Tracker

An app that identifies aircraft overhead from live ADS-B (Mode S) data. I built it in March 2024 as my IB Computer Science SL internal assessment.

## How it works

- **Server** (`Server/`, Node.js): connects over TCP to an ADS-B receiver's raw Mode S feed on port 30002 and decodes the messages, including each aircraft's ICAO address and its CPR-encoded position. It looks up registration, type and operator from the hexdb.io registry API, finds a photo of the aircraft on JetPhotos (axios and cheerio) with an in-memory cache, and serves the results over HTTP.
- **App** (`Frontend/ads-b-scaner/`, React Native with Expo): uses the phone's GPS (expo-location), motion sensors (expo-sensors) and camera to work out which aircraft the phone is pointed at and show its details.

## Running it

```
cd Server
npm install
node app.js
```

The server needs an ADS-B receiver feed on port 30002; set the receiver's address in `Server/app.js`. It serves HTTP on port 81.

```
cd Frontend/ads-b-scaner
npm install
npx expo start
```

## License

MIT

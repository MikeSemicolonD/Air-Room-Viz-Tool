# [Air Room Temperature Flow Visualization Tool](https://mikesemicolond.github.io/Air-Room-Viz-Tool/)

A static tool for *roughly* simulating air of different temperatures through a room.

## Why
They always tell you to open a window to "*let the heat out*". 

**Is that true?**

**Is it efficient?** 

I don't have the answers, but I hope this tool helps to provide some insight. ;)

## What it does

Set the room's size, ceiling shape, and the weather outside, then drop in whatever
moves air or makes heat — window ACs, box fans, ceiling registers, open windows and
doors, heaters, appliances, people, furniture. Drag it around in 3D (`Q` move,
`W` turn, `E` size) and watch the air sort itself out.

- **Views** — volumetric haze, a slice plane on any axis, drifting tracers, or an arrow field
- **Readouts** — mean air temperature, ceiling-to-floor spread, air changes per hour, humidity, solar gain, cooling load
- **Schedule** — capture the room at points through the day; settings ramp between them
- **Run** — play a full 24-hour cycle and chart mean vs. probe temperature
- **Presets** — bedroom, cross-vent living room, home office, ducted studio, kitchen exhaust, sealed baseline

Layouts persist in your browser and export as JSON.

## How rough is *roughly*?

It solves incompressible flow on a coarse grid — cells are half a foot or so — with
buoyancy, an eddy-diffusion stand-in for turbulence, heat stored in the surfaces, and
simple psychrometrics. Real airflow wants much finer cells and real turbulence
modelling, so read the numbers as directional, not as a load calculation.

## Running it locally

Any static file server works. Everything but the fonts is vendored:

```sh
python -m http.server
```

Then open <http://localhost:8000/>.

`index.html` is the whole tool — markup, solver, and renderer. `support.js` is the
Claude Design runtime that renders the template, and `vendor/` holds three.js and
React.

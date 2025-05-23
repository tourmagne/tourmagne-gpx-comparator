# How to use
## With node
- Add source gpx files in `data/inputs/reference_track` and `data/inputs/challenger_tracks` folders
- Run `npm run node`
- Synthesis is logged in the console.
- The gpx file containing all missed points of reference track is added in `data/output` folder

## In browser
- Run `npm run build` or `npm run build:watch` to bundle javascript files
- Launch you local server
- Open `http://localhost:5500` in your web browser

## Good to know
You can create test GPX files and view generated GPX files with https://gpx.studio/l/fr/.

# For devs only
## Deployed on github pages using Github Actions (and not the basic Deploy From Branch)
- Details in `.github/workflows/deploy.yml`

## Dev mode
- Use `webpack --mode=development` to avoid minification only in dev mode
- Launch all tests with `npm run test`

## Performance info
2 long methods (respectively with orleans-loop & Bordeaux_Paris examples):
  - parseGpx chall : 350 ms / 2300 ms
  - calculate closest: 7000 ms / 5000 ms
  - => Comes from external libs fast-xml-parser & calculateClosest (while loop executed 1_000_000 times)

## To do
- Optimize performance by using the hypothesis that points are really close together in `calculateClosest` method
- Check timestamps presence before calculating kpis
- Create personalized Error classes
- Get rid of global variables in indexWeb.js ?

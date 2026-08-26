# Morning Brief

A weather page for the things weather actually does to you — sunburn, pollen,
joints, migraines, bugs, mud, frost on the windshield, and whether the water is
safe to get into.

One static HTML file. No server, no build step, no account, no tracking.

**Live:** https://rhymes-with-tree.github.io/weather/

---

## What it does

Cards for the shape of the day — feels-like temperature, humidity, sun and
cloud, precipitation, daylight — each drawn as a gradient running midnight to
midnight, so the middle of the card is the middle of the day.

Then a grid of single facts, most of which only appear when they apply:
sunburn, frostbite, windshield frost, pipe freeze, fire weather, bugs, pavement
temperature, which shoes to wear, road salt, mowing, wind, frizz, basement
damp, arthritis, allergens, migraine, air quality, daylight exposure, aurora,
and the moon.

Tap any card for the numbers behind it and what to do about it.

Settings turn off whatever doesn't apply to you — no lawn, no car, no
basement, no dog, conditions you don't have. Everything is on to start with.

## Where the numbers come from

| Source | Used for | Licence |
|---|---|---|
| [Open-Meteo](https://open-meteo.com) | Forecast, air quality, marine, geocoding | Data CC BY 4.0 |
| [Copernicus CAMS](https://atmosphere.copernicus.eu) via Open-Meteo | Air quality when no Google key is set | Copernicus licence |
| [NOAA / National Weather Service](https://www.weather.gov) | Active alerts | US public domain |
| [CDC NWSS](https://www.cdc.gov/wastewater) | COVID, influenza A and RSV in state wastewater | US public domain |
| [Federal Register](https://www.federalregister.gov) | Presidential half-staff proclamations | US public domain |
| [Mast](https://www.mast.today) | State half-staff orders, **only** with a user's own key | Mast terms |

When Mast data is on screen, the card carries a *Powered by Mast* credit linking
back to them, as they ask. Nothing is shown when no Mast key is set.
| [NOAA CO-OPS](https://tidesandcurrents.noaa.gov) | Water temperature, coast and Great Lakes | US public domain |
| [NOAA NDBC](https://www.ndbc.noaa.gov) | Buoy water temperature and waves, where reachable | US public domain |
| [NOAA SWPC](https://www.swpc.noaa.gov) | Planetary K index, for aurora | US public domain |
| [Google Maps Platform](https://developers.google.com/maps) | Pollen and air quality, **only** if a user adds their own key | Google terms |

Open-Meteo's data is CC BY 4.0 and requires attribution. The app credits every
source in its own About panel as well as here.

Nothing is proxied. Every request goes straight from the visitor's browser to
the services above.

## Optional Google API key

Leave it blank and allergens come from a regional bloom calendar and air
quality from CAMS at roughly 45 km. Add a key with the Pollen and Air Quality
APIs enabled and you get measured pollen with named plants, plus air quality on
a 500 m grid with health guidance written for respiratory conditions.

The key is stored in the visitor's own browser and billed to whoever pasted it.
Hosting this costs the host nothing.

Each card says which source it used either way.

## Privacy

There is no account, no server, no analytics and no cookies. Settings and saved
places live in the visitor's browser via `localStorage`. Coordinates go to the
weather services listed above as part of each request, and nowhere else.

## Honest limits

- **US only.** Units are imperial throughout, NWS alerts are US-only, the air
  quality index is US EPA, and the bloom calendars cover six US regions.
- **Viral activity is state-level, not local.** It is genuinely measured rather
  than modelled, but it describes a whole state's wastewater and says nothing
  about your own risk. WastewaterSCAN feeds the same system and reports at
  sewershed level, but publishes under a non-commercial licence that asks users
  to make contact first, so this uses the CDC copy.
- **Most health cards are heuristics**, not validated instruments. Migraine,
  arthritis, bugs, frizz, shoes and mowing are rules written by hand from
  commonly cited triggers. The arthritis link in particular is widely reported
  and weakly evidenced — several large studies found little or no association.
- **Allergens without a Google key are modelled, not counted.** A regional
  bloom calendar adjusted for wind, humidity and rain. Cross-check a station
  count before trusting it.
- **Water temperature** tries an NDBC buoy first, then a NOAA CO-OPS shoreline
  gauge, then a modelled sea surface temperature. NDBC does not send CORS
  headers, so in a browser it is normally the CO-OPS gauge that answers. The
  card names its source and how far away it is; on a big lake, twenty miles of
  shore can differ by ten degrees after an upwelling.
- Thresholds are constants at the top of each card function and are meant to be
  tuned against your own record.

## Not medical advice

This page cannot tell you how you will feel. Don't use it to make decisions
about medication, treatment, or whether to seek care. For weather that could
hurt you, the National Weather Service is the authority. Water conditions in
particular change faster than any forecast — check local flags and signage
before you swim.

## Licence

See [LICENSE](LICENSE). The licence covers this code; the data sources above
carry their own terms.

# FeatherFind — Expanded Australian Bird Checklist

The guide contains **954 species**, with **eight detailed profiles** and **eight offline photo-ID candidates**. New records can be searched, favourited and saved as sightings. See [LARGE_CATALOGUE.md](LARGE_CATALOGUE.md) for source, scope and missing-data handling. Build the **FeatherFind** scheme.

Earlier version notes follow; references to an eight-species catalogue or hosted setup describe earlier releases.

# FeatherFind — Offline Photo ID

Photo identification now runs locally using a bundled BioCLIP-based Core ML prototype. Rebuild/reinstall the **FeatherFind** scheme. No hosted service or API key is required. See [OFFLINE_PHOTO_ID.md](OFFLINE_PHOTO_ID.md) for limitations, credits and verification. The approximately 165 MB model compares the eight guide species; only the supplied Galah example has been verified for recognition.

Earlier phase notes below describe previous versions and may refer to the superseded hosted-service setup.

# FeatherFind — Phase 5

Favourites, life-list totals and optional sighting map pins are included. See [PHASE5.md](PHASE5.md). Identification remains the opening screen. No live AI backend is connected.

# FeatherFind — Phase 4

Describe a Bird now supports multiple colours, distinctive features and ranked explanations. See [PHASE4.md](PHASE4.md) for usage, ranking rules and verification. Phase 3 camera and backend preparation remain included; no live identification service is connected.

# FeatherFind — Phase 3

Camera capture and the prepared identification connection are now included. No live model or service is configured. See [PHASE3.md](PHASE3.md) for setup, API contract and checks.

# FeatherFind — Phase 2

Native SwiftUI iPhone starter. iOS 17+, Xcode 15 or later. No packages, API keys, account or network access required. Source delivery, not an App Store release.

## Open and run

1. Extract the ZIP into a normal local folder.
2. Open `FeatherFind.xcodeproj`. Select the shared **MyApp** scheme.
3. Choose an iPhone simulator, then Product → Build (⌘B) and Run (⌘R).
4. For a physical iPhone, select the FeatherFind target → Signing & Capabilities → choose your development team and, if needed, a unique bundle identifier. The default identifier is `mattpinner.FeatherFind`.

No camera or location permission is requested. PhotosPicker gives access only to selected images. Camera capture is implemented; live AI identification awaits a backend. Selected images are not uploaded.

## Included

- Home, Identify, Bird Guide and Sightings tabs, each with a NavigationStack, in a dark forest palette.
- Eight Australian species in a bundled, versioned JSON catalogue. **Not a complete Australian checklist.** Includes native and locally introduced occurrences; state filters indicate broad presence, not detailed range or abundance.
- Search common/scientific names, families, colours and habitats. Combine family, state/territory, habitat, colour and size filters. Different filters use AND; each selected value is exact. Colour tags include different sexes/plumages, so they are broad aids.
- Species profiles: identification, family, size, habitat, distribution, diet, fact, reference and comparison links. Comparisons span this small sample and are not a complete lookalike set.
- Describe-a-bird filtering, with no invented confidence percentages.
- SwiftData sightings: save date, manually entered location, notes and optional selected photo; inspect and delete saved records. Species names are retained as snapshots if catalogue entries are later removed.
- Local asset photo rendering and visible credit/source/licence/change information. No third-party bird photos are bundled; placeholders are intentional. See PHOTO_ATTRIBUTION.md.

## Project layout

```
FeatherFind.xcodeproj/       Ready-to-open project and shared scheme
FeatherFind/
  App/                     App entry point and SwiftData container
  Models/                  Bird, PhotoCredit, BirdFilter, Sighting
  Data/                    Validated catalogue loader
  Resources/birds.json     Editable offline species catalogue
  Views/                   Four tabs, guide, detail, photos and sightings
Tools/                     Catalogue/filter verification
```

## This folder’s integration

Updated in place from the mixed Phase 1/Phase 2 project. Original signing team, bundle identifier, target name (`MyApp`) and asset catalogue are retained. Open FeatherFind.xcodeproj and select the MyApp scheme (or its automatically generated target scheme).

A Before-Phase2 ZIP in this folder contains the complete pre-update project. BirdSighting retains its original entity name and fields, with only an optional photoData property added for lightweight SwiftData migration. The original `magpie` and `superb-fairywren` catalogue IDs are retained. No store is deleted. Verify existing sightings on your device before distributing this update.

## Expand the catalogue

Use the existing JSON records as the schema. `schemaVersion` is currently 1. Keep `id` permanent: sightings and comparisons depend on it. Every `similarIDs` entry must resolve. Values used by filters are case-sensitive controlled vocabulary; copy existing spellings. A missing/invalid JSON file produces a visible load error instead of silently showing an empty guide.

The short summaries are starter editorial text with reference links, not copied bird-profile pages or an imported checklist. Review taxonomy, all regional tags and identification content against an authoritative versioned checklist before publishing expanded coverage. `reviewedOn` records this starter’s assembly date, not an expert audit. No conservation statuses or precise range maps are asserted.

References: BirdLife Australia species profiles (linked in each record), and the Australian Museum Eastern Yellow Robin profile. Reference-site photographs are not included or licensed by these text links.

## Manual acceptance checklist

- Open all four tabs; follow a Home featured species to its profile.
- Search “Eopsaltria”, “Cacatuidae” and mixed-case “gALah”.
- Select QLD + Pink: Galah remains. Select TAS + Yellow + Forest: robin is excluded.
- Try incompatible filters; verify the empty state and reset.
- Open a profile, follow comparison links and the external reference.
- Save two sightings with different dates and notes; add a photo to one. Relaunch, inspect both and delete one.
- Cancel a new sighting and verify that no record was added.
- Select a photo under Identify; verify that the app does not claim to identify it.
- Test larger accessibility text, VoiceOver and offline browsing on a simulator/device.

The archive contains no app icon; add your own Assets.xcassets and AppIcon before distribution.

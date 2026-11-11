# Art
Infrastructure for an artistic website

## Artist setup guide

This project is designed to be configured by an artist or curator without editing the HTML. The app loads its data from JSON files at runtime.

### Recommended file layout

Place the following files in the same directory as `index.html` and `gallery.html`:

```text
/
├── index.html
├── gallery.html
├── config.json
├── galleries.json
├── images.json
├── logo.jpeg
└── images/
    ├── cover-1.jpg
    ├── cover-2.jpg
    └── artwork-1.jpg
```

If you want to keep the JSON files in a different folder or remote hosting location, you can pass a `?config=` URL when opening the site.

### `config.json`

`config.json` is the main configuration file. It tells the app how to build the home page and where to find the rest of the data.

Example:

```json
{
  "brandName": "Mira Studio",
  "logoUrl": "logo.jpeg",
  "galleriesUrl": "galleries.json",
  "imagesUrl": "images.json",
  "searchPlaceholder": "Search artwork..."
}
```

Field descriptions:

- `brandName`: The brand or artist name shown in the header and page title.
- `logoUrl`: Relative or absolute path to your logo image.
- `galleriesUrl`: URL to the gallery catalog file.
- `imagesUrl`: URL to the artworks data file.
- `searchPlaceholder`: Placeholder text shown in the search box.

If `?config=` is not present, the app looks for a local `config.json` in the same folder as the HTML file.

### `galleries.json`

`galleries.json` contains the list of gallery cards shown on the home page.

Example:

```json
[
  {
    "title": "Portraits",
    "coverUrl": "images/portraits-cover.jpg",
    "searchCriteria": "portrait"
  },
  {
    "title": "City Light",
    "coverUrl": "images/city-light-cover.jpg",
    "searchCriteria": "city"
  },
  {
    "title": "Landscapes",
    "coverUrl": "images/landscapes-cover.jpg",
    "searchCriteria": "landscape"
  }
]
```

Field descriptions:

- `title`: Display name for the gallery card.
- `coverUrl`: Image used on the gallery card.
- `searchCriteria`: A keyword used to route the viewer and match the gallery in the search flow.

### `images.json`

`images.json` contains every artwork in the collection.

Example:

```json
[
  {
    "title": "Morning Light",
    "medium": "Oil on canvas",
    "year": 2025,
    "technic": "Layered glazing",
    "dimensions": "60 x 80 cm",
    "keywords": "sunrise, warm tones, landscape",
    "url": "images/morning-light.jpg"
  },
  {
    "title": "Night Window",
    "medium": "Digital print",
    "year": 2024,
    "technic": "Inkjet print",
    "dimensions": "50 x 70 cm",
    "keywords": "city, night, architecture",
    "url": "images/night-window.jpg"
  }
]
```

Field descriptions:

- `title`: Artwork title shown in the gallery viewer.
- `medium`: Material or format, such as `Oil on canvas` or `Photography`.
- `year`: Year the artwork was created.
- `technic`: Technique or process.
- `dimensions`: Physical size or format.
- `keywords`: Comma-separated keywords used for search matching.
- `url`: Relative or absolute path to the image file.

The search feature matches the query against `title`, `keywords`, and `medium`.

### Example URLs

Local setup:

```text
https://example.com/index.html
https://example.com/index.html?config=config.json
https://example.com/gallery.html?config=config.json&search=portrait
```

Remote or hosted JSON setup:

```text
https://example.com/index.html?config=https://cdn.example.com/config.json
https://example.com/gallery.html?config=https://cdn.example.com/config.json&search=landscape
```

The application resolves relative URLs from the location of the config file. This means that if your config is hosted remotely, image and JSON paths should be relative to that remote location or be fully qualified URLs.

### Quick example

If you host everything in a single folder, your files may look like this:

```text
index.html
gallery.html
config.json
images.json
galleries.json
logo.jpeg
images/
```

And the configuration file might be:

```json
{
  "brandName": "Adele Rowan",
  "logoUrl": "logo.jpeg",
  "galleriesUrl": "galleries.json",
  "imagesUrl": "images.json",
  "searchPlaceholder": "Search my paintings..."
}
```

This is enough for the site to render a working portfolio and gallery viewer.

## License

This project is licensed under the Boost Software License - Version 1.0.

Copyright information and the full license text are included in the repository's `LICENSE` file.

When redistributing this project or any derived work, please keep the copyright notice and the full license statement with the software, as required by the Boost Software License.

For source files, it is recommended to include a copyright header such as:

```text
Copyright (c) 2026 mkview

Distributed under the Boost Software License 1.0. See accompanying file LICENSE
```

This notice should be preserved in copies and derivative works of the software.

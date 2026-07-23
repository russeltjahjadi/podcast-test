# Podcast Test

This repository generates a podcast RSS feed from a YAML definition.

`feed.py` reads `feed.yaml` and produces `podcast.xml`, which can be used as a podcast RSS feed for audio hosting and directories.

## Project Structure

- `feed.py` — Python script that converts `feed.yaml` into `podcast.xml`
- `feed.yaml` — Podcast metadata and episode definitions
- `podcast.xml` — Generated RSS feed output
- `audio/` — Episode audio files referenced by the feed
- `images/` — Artwork and image assets for the podcast

## How it Works

The script loads the YAML file, builds an RSS feed with iTunes podcast tags, and writes the XML output.

The feed metadata includes:
- podcast title
- subtitle
- author
- description
- image path
- language
- category
- base link URL
- episode items

Each episode item includes:
- title
- description
- publication date
- duration
- audio file URL
- file length

## Requirements

- Python 3.8+ (or newer)
- `PyYAML` library

Install dependencies:

```bash
python -m pip install pyyaml
```

## Generate the Feed

Run the script from the repository root:

```bash
python feed.py
```

This creates or updates `podcast.xml` using the values defined in `feed.yaml`.

## Customize Your Podcast

Edit `feed.yaml` to update podcast metadata or add episodes.

- Update `link` to match the published feed base URL
- Use `/audio/<filename>.mp3` for episode media paths
- Use `/images/<filename>.jpg` for artwork
- Ensure `length` matches the actual file size in bytes

## Notes

- `podcast.xml` is generated automatically and should not be edited manually unless needed for testing.
- Keep audio files in `audio/` and artwork in `images/` so the generated feed references valid URLs.

## CI / GitHub Actions

This repository includes a GitHub Actions workflow at `.github/workflows/main.yml`.

The workflow:
- runs on every `push`
- checks out the repository using `actions/checkout@v3`
- invokes the `russeltjahjadi/podcast-generator@main` action to generate the podcast feed

That means the feed generation is delegated to another repository, `podcast-generator`, which is expected to contain the code or action definition for producing the final RSS feed.

## License

This repository is a simple utility for building a podcast XML feed from YAML source data.

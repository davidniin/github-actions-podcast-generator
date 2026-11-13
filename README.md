# Podcast Generator (GitHub Action)

A Docker-based GitHub Action that **generates a podcast RSS feed from a YAML file**. Describe the show and its episodes in `feed.yaml`; the action runs `feed.py`, builds the iTunes-compatible `podcast.xml` and commits it back to the repository.

## Usage

```yaml
# .github/workflows/main.yml
name: Podcast feed
on:
  push:
    branches: [main]
permissions:
  contents: write
jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: davidniin/gitthub-actions-podcast-generator@main
```

### Inputs

| Input | Description | Default |
|---|---|---|
| `name` | Committer name | `${{ github.actor }}` |
| `email` | Committer email | `${{ github.actor }}@localhost` |

A working example repository: [`podcast-test`](https://github.com/davidniin/podcast-test).

## Stack

Python (PyYAML, `xml.etree`) · Docker · GitHub Actions

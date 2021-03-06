# Fresh-bot

#### The opposite of [Stale](https://github.com/apps/stale). A bot against stale bots.

This GitHub Action will leave a comment in your name whenever a stale bot is about to close an issue you're subscribed to. _Let the fight begin._

## Why?

Issues don't go away just because you don't look. Many projects maintain a facade of good health by ignoring and auto-closing issues. Closed issues fragment the discussion and discourage outside contributions. It is often unclear whether an issue is still present. And so on. This scenario is a nightmare for developers.

## How?

The action checks notifications and acts when a bot comments a stale warning, usually something like "*This issue has been automatically marked as stale*". It will then make a comment if no one else did that yet.

## Usage

- Create a repo for running personal actions or use any repo
- Create a [Personal Access Token](https://github.com/settings/tokens) with `repo` scope and set it as a repository secret with the name `PERSONAL_ACCESS_TOKEN`
- Commit the workflow below

`.github/workflows/fresh-bot.yml`
```yml
name: Bump stale issues

on:
  schedule:
    # Run every day at 1am
    - cron: '0 1 * * *'

jobs:
  fresh-bot:
    runs-on: ubuntu-latest

    steps:
      - name: Bump stale issues
        uses: c-hive/fresh-bot@v1
        with:
          GITHUB_TOKEN: ${{ secrets.PERSONAL_ACCESS_TOKEN }} # Needs `repo` scope
```

## Conventions

This project follows [C-Hive guides](https://github.com/c-hive/guides) for code style, way of working and other development concerns.

## License

The project is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

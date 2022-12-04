# The Run API Docs

These API docs are still being built. The outline here is a generality without examples for those who want to use it early.

## User runs

The runs for a specific user can be accessed at `https://therun.gg/api/users/<username>`, which gives a list of runs by username with some basic info about the run. This fills the user profiles. Every run has a key "historyFileName", which can be used by going to `https://d1qsrp2avfthuv.cloudfront.net/<historyFileName>`. This url gives a bunch of detailed data about that specific run, which populates the run detail page. 

## Games
`https://therun.gg/api/games` gives an overview of all games currently on the site. Every game has a key `game`, which can be used to navigate to `https://therun.gg/api/games/<game>`, which gives a detailed overview for that game, including leaderboards under the `stats` key.

## Frontpage data
`https://therun.gg/api/frontpagedata` gives the data that's on the frontpage.

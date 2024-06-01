# Visit https://github.com/lowlighter/metrics#-documentation for full reference
name: Metrics
on:
  # Schedule updates (each hour)
  schedule: [{cron: "0 * * * *"}]
  # Lines below let you run workflow manually and on each commit
  workflow_dispatch:
  push: {branches: ["master", "main"]}
jobs:
  github-metrics:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: lowlighter/metrics@latest
        with:
          # Your GitHub token
          # The following scopes are required:
          #  - public_access (default scope)
          # The following additional scopes may be required:
          #  - read:org      (for organization related metrics)
          #  - read:user     (for user related data)
          #  - read:packages (for some packages related data)
          #  - repo          (optional, if you want to include private repositories)
          token: ${{ secrets.METRICS_TOKEN }}

          # Options
          user: https://github.com/Yzhiua
          template: classic
          base: header, activity, community, repositories, metadata
          base_hireable: yes
          base_indepth: yes
          config_display: columns
          config_octicon: yes
          config_timezone: Asia/Tokyo
          config_twemoji: yes
          plugin_music: yes
          plugin_music_limit: 4
          plugin_music_mode: recent
          plugin_music_played_at: yes
          plugin_music_provider: apple
          plugin_music_time_range: short
          plugin_music_top_type: tracks
          plugin_music_user: .user.login
          plugin_notable: yes
          plugin_notable_from: organization
          plugin_notable_indepth: yes
          plugin_notable_repositories: yes
          plugin_notable_self: yes
          plugin_notable_types: commit
          plugin_steam: yes
          plugin_steam_achievements_limit: 2
          plugin_steam_games_limit: 2
          plugin_steam_playtime_threshold: 2
          plugin_steam_recent_games_limit: 2
          plugin_steam_sections: player, most-played, recently-played
          plugin_steam_user: STEAM_0:1:552968923
          plugin_tweets: yes
          plugin_tweets_attachments: yes
          plugin_tweets_limit: 2
          plugin_tweets_user: .Yzhiua_Re.twitter

<h3 align="left">Hello, I'm Rhizz</h3>

###

<br clear="both">

<div align="center">
  <img src="https://raw.githubusercontent.com/maurodesouza/profile-readme-generator/master/src/assets/icons/social/linkedin/default.svg" width="52" height="40" alt="linkedin logo"  />
  <img src="https://raw.githubusercontent.com/maurodesouza/profile-readme-generator/master/src/assets/icons/social/twitter/default.svg" width="52" height="40" alt="twitter logo"  />
  <a href="https://www.instagram.com/rhizz.dev/" target="_blank">
    <img src="https://raw.githubusercontent.com/maurodesouza/profile-readme-generator/master/src/assets/icons/social/instagram/default.svg" width="52" height="40" alt="instagram logo"  />
  </a>
  <img src="https://raw.githubusercontent.com/maurodesouza/profile-readme-generator/master/src/assets/icons/social/telegram/default.svg" width="52" height="40" alt="telegram logo"  />
</div>

###

<div align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=HRhizzz&hide_title=false&hide_rank=false&show_icons=true&include_all_commits=true&count_private=true&disable_animations=false&theme=blue-green&locale=en&hide_border=false&order=1" height="" alt="stats graph"  />
  <img src="https://github-readme-stats.vercel.app/api/top-langs?username=HRhizzz&locale=en&hide_title=false&layout=compact&card_width=320&langs_count=6&theme=blue-green&hide_border=false&order=2" height="150" alt="languages graph"  />
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=HRhizzz&radius=16&theme=react&area=true&order=5" height="300" alt="activity-graph graph"  />
</div>

###

<img src="https://raw.githubusercontent.com/HRhizzz/HRhizzz/output/snake.svg" alt="Snake animation" />

###
name: Generate snake animation

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - master

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: dist/snake.svg?palette=github-dark


      - name: push snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

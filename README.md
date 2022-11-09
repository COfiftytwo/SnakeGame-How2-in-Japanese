# スネークゲーム - 日本語版！
<img src="https://raw.githubusercontent.com/Platane/snk/output/github-contribution-grid-snake.svg" width="790px" height="200px" />
今回はPlataneさんが作ったスネークゲームを使ってみましょう～

スネークゲームのGithubのマーケットプレイスはコチラから→https://github.com/marketplace/actions/generate-snake-game-from-github-contribution-grid


手順１：リポジトリを作成する
Repository nameは好き名前を。作成の際「Add a README file」にチェックを忘れないように～ 

手順２：yamlファイルを作る。
今回はyamlファイルについての説明はしません。リポジトリを作成すると、右上に「Add file」から「Create new file」をクリック～
「Name your file...」に「.github/workflows/～～.yaml」をコピペし～～を好きなファイル名に変更して、「Commit chenges」をクリック。

手順３：yamlファイルに下のコードをコピペする。
yamlファイルに下のコードをコピペして、「github_user_name:」の横に自分のユーザー名を書く。「Commit chenges」をクリック。

```
# GitHub Action for generating a contribution graph with a snake eating your contributions.

name: Generate Snake

# Controls when the action will run. This action runs every 6 hours.

on:
  schedule:
      # every 6 hours
    - cron: "0 */6 * * *"

# This command allows us to run the Action automatically from the Actions tab.
  workflow_dispatch:

# The sequence of runs in this workflow:
jobs:
  # This workflow contains a single job called "build"
  build:
    # The type of runner that the job will run on
    runs-on: ubuntu-latest

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:

    # Checks repo under $GITHUB_WORKSHOP, so your job can access it
      - uses: actions/checkout@v2

    # Generates the snake  
      - uses: Platane/snk@master
        id: snake-gif
        with:
          github_user_name: COfiftytwo　←ここにユーザー名を書く。COfiftytwoとは私のユーザー名なので消して自分のユーザー名を書いてください！
          # these next 2 lines generate the files on a branch called "output". This keeps the main branch from cluttering up.
          gif_out_path: dist/github-contribution-grid-snake.gif
          svg_out_path: dist/github-contribution-grid-snake.svg

     # show the status of the build. Makes it easier for debugging (if there's any issues).
      - run: git status

      # Push the changes
      - name: Push changes
        uses: ad-m/github-push-action@master
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          branch: master
          force: true

      - uses: crazy-max/ghaction-github-pages@v2.1.3
        with:
          # the output branch we mentioned above
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

手順４：READMEファイルに戻って下のコードをコピペする。
READMEファイルに戻って下のコードをコピペして、「COfiftytwo/COfiftytwo」のところを、「自分のユーザー名/今回作ったリポジトリ名」に変更して、「Commit chenges」をクリック。
完了！
```
![Snake animation](https://github.com/COfiftytwo/COfiftytwo/blob/output/github-contribution-grid-snake.svg)
```

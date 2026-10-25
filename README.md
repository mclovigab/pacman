Pac-Man no GitHub

Um jeito diferente de personalizar o perfil do GitHub usando uma animação do Pac-Man no gráfico de contribuições.

Como instalar

1. No seu repositório de perfil, crie o arquivo .github/workflows/main.yml.

2. Adicione o código abaixo:

name: Generate Pac-Man
on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:
  push:
    branches:
      - main
permissions:
  contents: write
jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - name: Generate Pac-Man
        uses: abozanona/pacman-contribution-graph@main
        with:
          github_user_name: ${{ github.repository_owner }}
      - name: Publish animation
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

3. Em Settings → Actions → General, habilite a permissão de escrita para o GitHub Actions.

4. Entre na aba Actions e execute o workflow.

Adicionando ao perfil

No README.md do seu perfil, adicione:

![Pac-Man](https://raw.githubusercontent.com/SEU_USUARIO/SEU_USUARIO/output/pacman-contribution-graph.svg)

Troque SEU_USUARIO pelo seu nome de usuário do GitHub.

A animação será gerada a partir do gráfico de contribuições da sua conta.

Referência

Projeto original: https://github.com/abozanona/pacman-contribution-graph
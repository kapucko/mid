# Web MID Solutions

Statický web postavený na [Jekylli](https://jekyllrb.com/), ktorý GitHub Pages zostaví automaticky pri každom pushnutí. Nič netreba buildovať ručne.

## Kde čo upraviť

| Čo chcem zmeniť | Súbor |
|---|---|
| Akýkoľvek text na stránke, nadpisy, texty tlačidiel, menu | `_data/texty.yml` |
| Telefón, e-mail, adresa, IČO, IČ DPH, termín voľnej kapacity | `_data/kontakt.yml` |
| Farby, písma, medzery | `assets/css/style.css` (blok `:root` hore) |
| Logo | `_includes/logo.html` a `assets/img/favicon.svg` |
| Poradie sekcií alebo skrytie sekcie | `index.html` |
| Rozloženie konkrétnej sekcie | `_includes/sekcie/*.html` |

Telefón a e-mail sú zapísané len raz v `_data/kontakt.yml` a web ich použije všade, kde sú potrebné (kontakt, pätička, tlačidlá). Rovnako texty tlačidiel v `_data/texty.yml` → `tlacidla`.

### Pravidlá pre `.yml` súbory

- Meňte len text za dvojbodkou, názov pred ňou nechajte.
- Ak text obsahuje dvojbodku `:`, dajte ho celý do úvodzoviek `"..."`.
- Pri dlhších textoch (riadok končí `|`) je text odsadený pod ním. Prázdny riadok = nový odsek, `**takto**` = tučné písmo.
- Odsadenie musí byť medzerami, nie tabulátorom.

## Zverejnenie na GitHub Pages

1. Vytvorte repozitár na GitHube a nahrajte doň obsah tohto priečinka.
2. V repozitári: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, vetva `main`, priečinok `/ (root)`.
3. Po minúte až dvoch je web na adrese `https://<meno>.github.io/<repozitár>/`.
4. Ak web beží na takejto adrese s názvom repozitára, nastavte v `_config.yml` hodnotu `baseurl: "/<repozitár>"`. Inak sa nenačítajú štýly.

### Vlastná doména (napr. midsolutions.sk)

1. V **Settings → Pages → Custom domain** zadajte doménu. GitHub vytvorí súbor `CNAME`.
2. U registrátora domény nastavte DNS podľa [návodu GitHubu](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site).
3. V `_config.yml` nastavte `url: "https://www.vasadomena.sk"` a `baseurl: ""`.
4. Zapnite **Enforce HTTPS**.

## Lokálny náhľad (nepovinné)

Potrebujete Ruby. Potom v tomto priečinku:

```bash
bundle install
bundle exec jekyll serve
```

Web bude na `http://localhost:4000`. Zmeny v `_data/*.yml` sa prejavia po reštarte príkazu.

## Štruktúra

```
_config.yml          nastavenia webu (názov, adresa)
_data/texty.yml      všetky texty
_data/kontakt.yml    kontaktné a firemné údaje
_layouts/default.html  kostra stránky
_includes/           opakujúce sa časti (hlavička, pätička, logo, tlačidlo)
_includes/sekcie/    jednotlivé sekcie úvodnej stránky
assets/css/style.css štýly
assets/img/          favicon, neskôr fotky z realizácií
index.html           úvodná stránka (poradie sekcií)
404.html             stránka pre neexistujúci odkaz
```

# Veille médias — Arcom & CDJM

Dashboard public de suivi des décisions réglementaires et des avis déontologiques sur les médias français.

🔗 **[media-watch.github.io/veille-medias-fr](https://media-watch.github.io/veille-medias-fr/)**

---

## Sources

**Arcom** (Autorité de régulation de la communication audiovisuelle et numérique)
Décisions sur les 4 chaînes d'info en continu : BFM TV, CNews, LCI, Franceinfo.
Types suivis : Interventions, Mises en garde, Mises en demeure, Sanctions financières.
Source : [arcom.fr](https://www.arcom.fr/se-documenter/espace-juridique/decisions)

**CDJM** (Conseil de Déontologie Journalistique et de Médiation)
Avis fondés et partiellement fondés, tous médias confondus.
Source : [cdjm.org](https://cdjm.org/decisions/)

## Mise à jour automatique

Un workflow GitHub Actions tourne chaque lundi à 6h UTC :
- `scraper.py` récupère les nouvelles décisions Arcom
- `scraper_cdjm.py` récupère les nouveaux avis CDJM
- Les données sont injectées dans `index.html` et committées si elles ont changé

## Structure

```
index.html        Dashboard (données inline, fonctionne sans serveur)
decisions.json    Décisions Arcom (57 entrées)
cdjm.json         Avis CDJM (321 entrées)
scraper.py        Scraper Arcom (BeautifulSoup)
scraper_cdjm.py   Scraper CDJM (API JSON publique)
requirements.txt  Dépendances Python
```

## Lancer les scrapers localement

```bash
pip install -r requirements.txt
python scraper.py        # met à jour decisions.json et index.html
python scraper_cdjm.py   # met à jour cdjm.json et index.html
```

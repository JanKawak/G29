## Dataset and Preprocessing

Voor dit project combineren we meerdere internationale datasets om te onderzoeken hoe sociale hulpdiensten, vrijheid, politieke betrokkenheid en sociaal gedrag samenhangen met nationaal geluk, mentale gezondheid en welzijn.

### Gebruikte datasets

#### 1. Happiness Cantril Ladder  
**Bron:** [Our World in Data](https://ourworldindata.org/grapher/happiness-cantril-ladder)  
**Beschrijving:**  
Bevat per land en jaar de gemiddelde levensvoldoening, gemeten via de Cantril Ladder (schaal 0–10).  

**Relevante variabelen:**  
- `Entity`: Land  
- `Year`: Jaar  
- `Life Ladder`: Gemiddelde geluksscore  

#### 2. Mental Health Dataset  
**Bron:** [Kaggle](https://www.kaggle.com/datasets/imtkaggleteam/mental-health)  
**Beschrijving:**  
Zelfgerapporteerde gegevens over het voorkomen van mentale aandoeningen, zoals depressie en angststoornissen.  

**Relevante variabelen:**  
- `Entity`: Land  
- `Year`: Jaar  
- `Depressive_disorders`: Percentage mensen met een depressiestoornis  
- `Anxiety_disorders`: Percentage mensen met een angststoornis  

#### 3. Suicide Rates Dataset  
**Bron:** [Kaggle](https://www.kaggle.com/code/lmorgan95/r-suicide-rates-in-depth-stats-insights/input)  
**Beschrijving:**  
Aantal zelfmoorden per land, per jaar, inclusief uitsplitsingen naar leeftijd en geslacht.  

**Relevante variabelen:**  
- `country`: Land  
- `year`: Jaar  
- `suicides/100k pop`: Zelfmoorden per 100.000 inwoners  

#### 4. Comparative Political Dataset (CPDS)  
**Bron:** [CPDS Data](https://cpds-data.org/data/)  
**Beschrijving:**  
Gedetailleerde informatie over overheidsuitgaven aan sociale zekerheid, gezondheidszorg, onderwijs en andere sociale voorzieningen, per land en jaar.  

**Relevante variabelen:**  
- `country`: Land  
- `year`: Jaar  
- `socexp_c_pmp`: Sociale uitgaven in cash (% van het BBP)  
- `socexp_k_pmp`: Sociale uitgaven in natura (% van het BBP)  

#### 5. Happiness and Life Satisfaction - Politics Dataset  
**Bron:** [Our World in Data](https://ourworldindata.org/happiness-and-life-satisfaction)  
**Beschrijving:**  
Meet hoe belangrijk mensen politiek vinden in hun leven, per land en per jaar.  

**Relevante variabelen:**  
- `Entity`: Land  
- `Year`: Jaar  
- `Very important in life: Politics`: Percentage mensen dat politiek 'heel belangrijk' vindt  

#### 6. Mental Health and Lifestyle Dataset  
**Bron:** [Zenodo](https://zenodo.org/records/14838680)  
**Beschrijving:**  
Grote dataset met informatie over mentale gezondheid, leefstijl, werkuren, slaap, alcoholgebruik en roken.  

**Relevante variabelen:**  
- `Alcohol_Consumption`: Alcoholgebruik per persoon per jaar (liter)  

#### 7. Freedom House Dataset  
**Bron:** [Freedom House](https://freedomhouse.org/report/freedom-world)  
**Beschrijving:**  
Bevat per land de jaarlijkse vrijheidsscores en vrijheidsstatus (vrij, gedeeltelijk vrij, niet vrij).  

**Relevante variabelen:**  
- `Entity`: Land  
- `Vrijheidsscore (0-100)`: Score op vrijheid (0 = niet vrij, 100 = volledig vrij)  
- `Vrijheidsstatus`: Classificatie (vrij, gedeeltelijk vrij, niet vrij)  

---

## Preprocessing-stappen

Om de datasets geschikt te maken voor gecombineerde analyse en visualisatie zijn de volgende preprocessing-stappen uitgevoerd:

- **Selectie van relevante variabelen:**  
  Alleen variabelen die direct aansluiten bij de onderzoeksvragen zijn behouden, waaronder geluksscores, sociale uitgaven (cash en in natura), mentale aandoeningen, zelfmoordcijfers, politieke betrokkenheid, vrijheidsscores en alcoholgebruik.

- **Harmonisatie van landnamen:**  
  Landnamen zijn gestandaardiseerd over datasets heen (bijv. *United States of America* → *United States*) om samenvoegen mogelijk te maken.

- **Filtering op tijdsperiode en landen:**  
  - Voor de analyse rond sociale hulpdiensten is gefilterd op de periode 2011–2016.  
  - Voor de analyse rond vrijheid en politiek is gewerkt met het meest recente gemeenschappelijke jaar met voldoende data (2012).  
  - Landen met ontbrekende data in een van de kernvariabelen zijn verwijderd.

- **Opschonen en hernoemen van kolommen:**  
  Kolomnamen zijn geharmoniseerd naar uniforme Engelse stijl, spaties en onnodige tekens zijn verwijderd.

- **Samenvoegen datasets:**  
  De originele bronnen zijn gecombineerd op land- en jaar-niveau. Dit heeft geleid tot samengestelde werkbestanden, waaronder:  
  - *mental_welfare_dataset.csv* voor analyses rond sociale hulpdiensten en geluk  
  - *Gecombineerde_dataset__Politiek_belang__alcoholconsumptie_en_geluk.csv* voor analyses rond politiek, vrijheid, alcoholgebruik en geluk  
  - *Gecombineerde_dataset_met_extra_vrijheid.csv* voor de uitgebreide vrijheid-analyse  

- **Bepaling van indicatoren:**  
  Sociale uitgaven zijn opgesplitst in cash-uitgaven en in-natura hulpdiensten. Vrijheid is zowel als numerieke score als als categorie (vrij, gedeeltelijk vrij, niet vrij) meegenomen.

**Correlatie-analyse en filtering:**  
Binnen de sociale uitgaven zijn alleen indicatoren met een duidelijke positieve correlatie (r ≥ 0.4) met geluk behouden voor visualisatie in de heatmap. Dit zijn:
- `socexp_k_pmp`: Sociale uitgaven in natura (% van het BBP)  
- `homehelp_pmp`: Uitgaven aan thuishulp voor ouderen en zieken  
- `childcare_pmp`: Uitgaven aan kinderopvang  
- `family_pmp`: Uitgaven aan gezinsvoordelen  
- `health_pmp`: Overheidsuitgaven aan gezondheidszorg  
Deze indicatoren vertonen in de data het sterkste positieve verband met de Cantril-geluksscore en zijn daarom meegenomen in de verdere analyse.

## Samenvatting
Dankzij deze preprocessing zijn de datasets geschikt gemaakt voor de twee perspectieven van dit project:

1. **Sociale hulpdiensten en welzijn:**  
   We onderzoeken hoe in-natura hulpdiensten bijdragen aan geluk en mentale gezondheid, en vergelijken dit met de effecten van cash-uitkeringen.
2. **Vrijheid, politiek en sociaal gedrag:**  
   We analyseren hoe vrijheid, politieke betrokkenheid en sociaal gedrag (alcoholgebruik) samenhangen met geluk.

De preprocessing sluit direct aan op de interactieve visualisaties en statistische analyses die in het project gepresenteerd worden.

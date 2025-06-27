## Dataset and Preprocessing
We combineren internationale datasets om te onderzoeken hoe sociale hulpdiensten, vrijheid, politieke betrokkenheid en sociaal gedrag samenhangen met geluk, mentale gezondheid en welzijn.

### Gebruikte datasets
#### 1. Happiness Cantril Ladder  
**Bron:** [Our World in Data](https://ourworldindata.org/grapher/happiness-cantril-ladder)  
Gemiddelde levensvoldoening per land en jaar (Cantril Ladder, schaal 0–10).  
**Variabelen:**  
- `Entity`: Land  
- `Year`: Jaar  
- `Life Ladder`: Geluksscore  

#### 2. Mental Health Dataset  
**Bron:** [Kaggle](https://www.kaggle.com/datasets/imtkaggleteam/mental-health)  
Percentage mensen met depressie- en angststoornissen per land en jaar.  
**Variabelen:**  
- `Entity`: Land  
- `Year`: Jaar  
- `Depressive_disorders`: Depressie (%)  
- `Anxiety_disorders`: Angststoornissen (%)  

#### 3. Suicide Rates Dataset  
**Bron:** [Kaggle](https://www.kaggle.com/code/lmorgan95/r-suicide-rates-in-depth-stats-insights/input)  
Zelfmoorden per 100.000 inwoners, per land en jaar.  
**Variabelen:**  
- `country`: Land  
- `year`: Jaar  
- `suicides/100k pop`: Zelfmoorden per 100.000 inwoners  

#### 4. Comparative Political Dataset (CPDS)  
**Bron:** [CPDS Data](https://cpds-data.org/data/)  
Overheidsuitgaven aan sociale voorzieningen per land en jaar.  
**Variabelen:**  
- `country`: Land  
- `year`: Jaar  
- `socexp_c_pmp`: Sociale uitgaven in cash (% BBP)  
- `socexp_k_pmp`: Sociale uitgaven in natura (% BBP)  

#### 5. Happiness and Life Satisfaction - Politics Dataset  
**Bron:** [Our World in Data](https://ourworldindata.org/happiness-and-life-satisfaction)  
Hoe belangrijk mensen politiek vinden, per land en jaar.  
**Variabelen:**  
- `Entity`: Land  
- `Year`: Jaar  
- `Very important in life: Politics`: Politiek belangrijk (%)  

#### 6. Mental Health and Lifestyle Dataset  
**Bron:** [Zenodo](https://zenodo.org/records/14838680)  
Alcoholgebruik per persoon per jaar.  
**Variabelen:**  
- `Alcohol_Consumption`: Liter alcohol per persoon per jaar  

#### 7. Freedom House Dataset  
**Bron:** [Freedom House](https://freedomhouse.org/report/freedom-world)  
Vrijheidsscores en vrijheidsstatus per land.  
**Variabelen:**  
- `Entity`: Land  
- `Vrijheidsscore (0-100)`: Vrijheidsscore  
- `Vrijheidsstatus`: Vrij, gedeeltelijk vrij, niet vrij  

---

## Preprocessing-stappen

- **Selectie variabelen:** Alleen variabelen die aansluiten bij de onderzoeksvraag zijn behouden (geluk, sociale uitgaven, mentale aandoeningen, zelfmoorden, politieke betrokkenheid, vrijheid, alcoholgebruik).
- **Harmonisatie landnamen:** Landnamen gestandaardiseerd (bijv. *United States of America* → *United States*).
- **Filtering op tijd en landen:**  
  - Sociale hulpdiensten: periode 2011–2016.  
  - Vrijheid en politiek: jaar 2012 (meest complete jaar).  
  - Landen met ontbrekende kerndata verwijderd.
- **Opschonen kolomnamen:** Engelse stijl gehanteerd, spaties en onnodige tekens verwijderd.
- **Samenvoegen datasets:** Gecombineerd op land- en jaarniveau tot:  
  - *mental_welfare_dataset.csv* (sociale hulpdiensten & geluk)  
  - *Gecombineerde_dataset__Politiek_belang__alcoholconsumptie_en_geluk.csv* (politiek, vrijheid, alcoholgebruik & geluk)  
  - *Gecombineerde_dataset_met_extra_vrijheid.csv* (uitgebreide vrijheid-analyse)  
- **Bepaling indicatoren:**  
  - Sociale uitgaven opgesplitst in cash en in-natura.  
  - Vrijheid zowel numeriek (score) als categorisch (vrij, gedeeltelijk vrij, niet vrij).  
- **Correlatie-analyse en filtering:**  
  Alleen sociale indicatoren met positieve correlatie (r ≥ 0.4) met geluk zijn meegenomen in de heatmap:  
  - `socexp_k_pmp`: Sociale uitgaven in natura  
  - `homehelp_pmp`: Thuishulp ouderen/zieken  
  - `childcare_pmp`: Kinderopvang  
  - `family_pmp`: Gezinsvoordelen  
  - `health_pmp`: Gezondheidszorg  
Deze indicatoren vertonen het sterkste positieve verband met de Cantril-geluksscore en zijn daarom meegenomen in de verdere analyse.

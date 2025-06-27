
## Dataset and Preprocessing
Voor dit project maken we gebruik van zes verschillende datasets die samen inzicht geven in de relatie tussen mentale gezondheid, geluk en maatschappelijke factoren op internationaal niveau. Hieronder beschrijven we de datasets en de belangrijkste preprocessing-stappen die we hebben uitgevoerd.

# Datasetbeschrijvingen
### Happiness Cantril Ladder  
**Bron:** [Our World in Data](https://ourworldindata.org/grapher/happiness-cantril-ladder)  
Deze dataset bevat per land en per jaar de gemiddelde score van levensvoldoening (geluksscore), gemeten via de Cantril Ladder (schaal 0–10). Dit geeft een direct beeld van hoe gelukkig mensen zichzelf beoordelen.

### Mental Health Dataset  
**Bron:** [Kaggle](https://www.kaggle.com/datasets/imtkaggleteam/mental-health)  
Bevat gegevens over het voorkomen van depressieve en angststoornissen, gebaseerd op enquêtes en screeningsvragenlijsten.

### Suicide Rates Dataset  
**Bron:** [Kaggle](https://www.kaggle.com/code/lmorgan95/r-suicide-rates-in-depth-stats-insights/input)  
Geeft per land en per jaar het aantal zelfmoorden weer, inclusief uitsplitsingen naar leeftijd en geslacht.

### Happiness and Life Satisfaction - Politics Dataset  
**Bron:** [Our World in Data](https://ourworldindata.org/happiness-and-life-satisfaction)  
Meet hoe belangrijk mensen politiek vinden in hun leven, weergegeven per land en per jaar.

### Comparative Political Dataset (CPDS)  
**Bron:** [CPDS Data](https://cpds-data.org/data/)  
Gedetailleerde dataset met onder andere overheidsuitgaven aan sociale zekerheid, onderwijs en gezinstoelagen, voor 36 landen over de periode 1960–2022.

### Mental Health and Lifestyle Dataset  
**Bron:** [Zenodo](https://zenodo.org/records/14838680)  
Een grootschalige dataset (50.000 records) met informatie over mentale gezondheid, werkuren, slaappatroon, alcoholgebruik, roken en andere leefstijlfactoren.


## Preprocessing stappen

Om de datasets te combineren en bruikbaar te maken voor analyse en visualisatie, hebben we de volgende preprocessing-stappen uitgevoerd:

### Selectie van relevante variabelen
Uit de oorspronkelijke datasets hebben we alleen de variabelen geselecteerd die aansluiten bij onze perspectieven, zoals geluksscore, mentale aandoeningen, zelfmoordcijfers, sociaal vangnet en politieke betrokkenheid.

### Opschonen van kolomnamen
Kolomnamen zijn gestandaardiseerd naar een eenduidig Engels formaat om samenvoegen en analyse te vergemakkelijken.

### Filtering op tijdsperiode en landen
Alle datasets zijn gefilterd op de meest recente jaren waarvoor voldoende data beschikbaar is (grotendeels tussen 2010–2022) en alleen landen die in álle relevante datasets voorkomen zijn behouden.

### Verwijderen van ontbrekende waarden
Records met ontbrekende of onbetrouwbare gegevens zijn verwijderd, met name binnen de datasets over mentale aandoeningen en zelfmoordcijfers.

### Samenvoegen datasets
De datasets zijn samengevoegd op basis van land en jaar, zodat we integrale vergelijkingen kunnen maken tussen geluk, mentale gezondheid en maatschappelijke factoren.

### Berekenen van nieuwe variabelen
Voor enkele indicatoren, zoals overheidsuitgaven aan het sociaal vangnet of werkdruk, zijn nieuwe samengestelde variabelen berekend op basis van de ruwe data.

### Normaliseren van variabelen
Bepaalde variabelen, zoals zelfmoorden per 100.000 inwoners, zijn genormaliseerd om landen met verschillende bevolkingsomvang goed te kunnen vergelijken.



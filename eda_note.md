## About the dataset

### Columns

- **gni_capita**: gross national income per capita.
- **gghe-d**: domestic general government health expenditure (GGHE-D) as percentage of gross domestic product (GDP) (%)
- **che_gdp**: current health expenditure (CHE) as percentage of gross domestic product (GDP) (%)
- **une_poverty**: poverty headcount ratio at $1.90 a day (PPP) (% of population)

## 1. EDA
----
### Basic analysis
- **target feature** : 
    - WHO source : "life_expect" and why not "life_expect60", outlier (min value) = 2010 Haiti earthquake
    - UNICEF source : "une_life", outlier (min value) = Sierra Leone war (1991 – 18 janv. 2002)
    - une_life looks more stable (less outliers), but then maybe less truthful ?

- **nb columns/rows** : 32 columns / 3111 rows

- **columns types** : 28 floats, 3 objects/category-like, 1 int ('year' col => may need casting).
Float types cols are mainly rates per n-pop or percentages.

- **missing values** : 
    - "hospitals" has 95% missing data => non usable.
    - top missing values : hospitals (95%), pop education indicator cols from Unicef (school: 74%, edu_spend: 41%, literacy: 81%, poverty: 70%)
    - perfect correlation between vaccinations data (measles, polio and diphtheria). When 1 of those is missing, so are the others.
    - vacc data tends to miss when "basic_water" is missing (0.8 corr).
    - when "alcohol" value is missing, some pop health values too : vacc data (0.6), pop body shape (0.7)

Some correlation between mising values can indicate a variable correlation.  
I decided that cols with >80% missing values won't be considered.

### Indicators
I believe that each column can be categorized in indicators :
- **Mortality** : adult_mortality, infant_mort, age1-4mort
- **Government** : gghe-d, che_gdp, edu_spent
- **Population Health** : 
    - health coverage : vaccinations, hospitals, doctors
    - sanitary : basic_water, alcohol
    - physical shape : bmi, age5-19thinness, age5-19obesity
- **Living standard**: poverty, gni_apita, une_gni
- **Education** : schools

That doesn't necessarily mean that we should explicitly do a classification work on the dataset. 
But for the analysis, we could identify and group variables to visualize their relation with the target.

### In-depth analysis
- **target visualisation**:
    - an outlier for Haiti (2010 seism)
- **variable signification**:
- **correlations variables/target**:
    1. mortality : strongly correlated with target.
    2. pop health :
    3. government :
    4. living standard :
    5. education :
    
### First conclusions

### Advanced analysis

- **Analysis per year**
    - target :
        - Africa has the lowest life_exp => verified by high mortality rates while 
        - Europe has a higher one => close to Americas, Eastern Mediteranea and South Asia
    - mortality :
    - pop health :
    - living standard :
    - education :
    - blend this analysis with regions to create new informations

- **Analysis per region**
    - target :
        - Africa has the lowest life_exp => verified by high mortality rates while 
        - Europe has a higher one => close to Americas, Eastern Mediteranea and South Asia
    - mortality :
    - pop health :
    - living standard :
    - education :
    - profiling regions can help us to identify what indicators raise or lower life_expect

- **correlations between indicators**:
    1. mortality / mortality :
    2. mortality / pop health :
        - health coverage :
        - physical shape :
        - perks :
    3. mortality / politics :
    4. mortality / social :
    5. pop health / pop health :
    6. pop health / politics :
    7. pop health / social :

### Comparing coutries
- Plot maps with different indicators as the hue.
- Profile coutries from their global pop health.

## 2. Hypothesis / Intuitions / Ideas
----

**Hypothesis 1** : "Population health explains significantly mortality rates and thus gives a good idea of a country's life expectancy".
In other words, good pop health means low mortality rates and a high life expectancy.

- Visualize the evolution of the target with the evolution of pop health over the years
- Polio is mainly an infantile disease (< 5y olds) : check correlation between infantile death rate and polio vaccination rate
- Do the same for every other diseases in the dataset


## 3. Pre-processing

## 4. Feature selection

## 5. Model selection

## Final thoughts

- This dataset doesn't provide any data about political conflicts or wars => can affect gradually a country/region life expectancy
- The ML model is very sensible to noise => deadly natural disasters(ex : 2010 Haiti seism outlier)
# ReMa-DH-TEAM3

## Project Overview


## Data Acquisition
The original dataset on which we based our adapted dataset is from [Benden et al. (2021)](https://openhumanitiesdata.metajnl.com/articles/10.5334/johd.39).

### (1) Dataset description
Object name: Maritime Pirate Attacks Dataset
Format names and versions: CSV files
Creation dates: 3/2/2021
Language: English
License: Creative Commons Attribution-ShareAlike 4.0 International License
Repository name: Zenodo
Publication date: 2021-03-04

### (2) Codebook (adopted from Benden et al. 2021)
**Pirate Attacks**
- **Date [Key]** - Date of Attack. Ysed as a key with the Country Matrix data frame.
- **Time** - Time the attack took place, either in UTC or Local Time.
- **Longitude** - Longitude where the attack took place
- **Latitude** - Latitude where the attack took place
- **Attack type** - Either NA (Missing), Attempted, Boarding, or Hijacked.
- **Location Description** - A text description of the location. With attacks taking place at sea, it is not as simple as just naming a city or town.
- **Nearest Country [Key]** - The country code whose shore is closest to the attack. The resolution is around 1 km, it can be much better depending on how detailed the mapping of the coast is in the vicinity.
- **EEZ Country [Key]** - The Exclusive Economic Zone country code in which the attack took place, if it took place within an EEZ.
- **Shore Distance** - Distance in kilometres to the shore from the attack location. This is the true geographic distance over the surface of the earth.
- **Shore Longitude** - The longitude of the closest point on the shore to the attack.
- **Shore Latitude** - The latitude of the closest point on the shore to the attack.
- **Attack Description** - The text description of the attack if it exists.
- **Vessel Name** - The name of the ship which was attacked if it is known.
- **Vessel Type** - The type of vessel attacked if known.
- **Vessel Status** - The status of the ship at the time it was attacked. Either NA (Missing), Berthed (Tied to a berth), Anchored (anchored at sea or in a harbour), or Steaming (ship underway).

**Country Indicators**
- **Country [Key]** - The country in ISO3 country code format.
- **Corruption Index** - Corruption Perceptions Index.
- **Homicide Rate** - Total Intentional Homicides per 100,000 people.
- **GPD** - Gross Domestic Product (US Dollars).
- **Total Fisheries Per Ton** - Total Fisheries Production (metric tons).
- **Total Military** - Total Number of Armed Forces personnel.
- **Population** - Country Population.
- **Unemployment Rate** - Percentage of the Country Unemployed.
- **Total GR** - Total Government Revenue. An indication of how well the country collects taxes.
- **Industry** - Industrial contribution to total GDP.

**Country Codes**
- **Country [Key]** - The country in ISO3 country code format.
- **Region** - The region the country is in.
- **Country Name** - The English country name

## Methodology

### Task Divion:
- Giulia: Python
- Jelmer: QGIS
- Eveline: Github

## Workflow Steps


## Challenges and Solutions

One of the challenges we encountered while working on this project was the inconsistency of the use of the terms _boarding_ and _boarded_ in the original dataset. We first decided on 

## Ethical Considerations


## Results


## Documentation and Sustainability


## Reflection

### Meeting 1: 27th of April


### Meeting 2: 1st of May


### Meeting 3: 4th of May


### Meeting 4: 12th of May
Decisions made - We are going to look into the following time-periods: 1998-2003 & 2006-2011

## Authors
G. Massaggia, J. Groenenboom and E.J. Miedema.

## Acknowledgements
This data set would not have been possible without the work of [International Maritime Bureau (IMB)](https://icc-ccs.org/), [Professor Brandon C. Prins](https://brandonprins.weebly.com/index.html) and [Benden et al. (2021)](https://openhumanitiesdata.metajnl.com/articles/10.5334/johd.39).

## Competing Interests
The authors have no competing interests to declare.

## References
Benden, P., Feng, A., Howell, C., & Dalla Riva G. V. (2021). Crime at Sea: A Global Database of Maritime Pirate Attacks (1993–2020). Journal of Open Humanities Data, 7: 19, pp. 1–6. DOI: https://doi.org/10.5334/johd.39

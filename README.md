# ReMa-DH-TEAM3

## Project Overview
Previous research has indicated that from a global perspective, succesful pirate attacks are more likely to happen in regions that are relatively poor, have a fragile economy, and have decreasing military expenditure (Okeahalam & Otwombe, 2016). In a review of existing prediction models, Daxecker and Prins (2012) in addition found that geographic factors such as coastline length, population size, regional trade and peace years influenced the occurrence of pirate attacks, though predictore varied in significance between hijacking and other piracy incidents. This project investigates maritime piracy attack patterns during two significant surge periods, 1998–2003 and 2006–2011, as identified by Rivas Pardo (2021), using Benden et al.’s Global Database of Maritime Pirate attacks (2021). 
This project aims to build in particular on work done by Daxecker & Prins (2012), who found that GDP showed a statistically significant correlation with piracy incidents, and Rivas Pardo (2021), who identified the two main ‘surge periods’ in the amounts of pirate attacks per year. It does this by asking whether there is a significant difference between the GDP levels of the countries where three different types of pirate attacks identified in the database of the International Maritime Bureau (IMB), namely the ‘attempted’, ‘boarded’, and ‘hijacked’ categories, tend to occur during both of the surge periods identified by Rivas Pardo. This project takes a descriptive and exploratory approach, where GDP is not treated as a causal predictor of attack types: rather, it aims to observe whether the three attack types cluster around systematically higher or lower national GDPs compared to one another and whether this association shifts between the two surge periods. To support this analysis, QGIS is employed to spatially visualize the distribution of attack types alongside GDP levels across the affected countries, allowing geographic patterns to be examined alongside the economic ones.

<img width="1389" height="490" alt="overall_attacks" src="https://github.com/user-attachments/assets/089a84f8-128e-4edd-8a30-fb874c89ad47" />

<img width="1489" height="490" alt="overall_attackGDP" src="https://github.com/user-attachments/assets/774100de-b912-47f9-87db-4786edc9ab73" />


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

### (2) Sources (primarily adopted from Benden et al. 2021)
The piracy attack data from 1993 to 2014 was sourced from a dataset published by Daxecker & Prins ([2015](https://doi.org/10.1080/03050629.2015.1016159)), which was again sourced from the IMB. The data from 2014 to 2020 was web scraped from the IMB website ([IMB Piracy Reporting Centre, 2020](https://www.icc-ccs.org/piracy-reporting-centre)) using Julia .........

### (3) Codebook (adopted from Benden et al. 2021)
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

### QGIS
Pirate attacks
1. Load all the pirate attacks per year .CSV files into QGIS as point coordinates, so that they set the CRS for the rest of the files accurately (this should be EPSG:4326 - WGS 84)
2. create a categorized symbology based on attack type, with symbology set as follows:
   ![symbology](img/image2.png)
with ‘hijacked’ red, ‘boarded’/’boarding’ as light orange, and ‘attempted’ as green.
3. Ucheck any categories except ‘boarded’, ‘boarding’, ‘attempted’, and ‘hijacked’
4. Repeat this process for all years

GDP/EEZs
1. Load in the EEZ shapefile
2. Load in the GDP .CSV files for 2006-2011 with no geometry
3. In the Processing Toolbox, find ‘join attributes by field value’ (Vector General)
4. As input layer, set the EEZ shapefile. As input layer 2, set the GDP table. Set table fields to the columns that refer to the ISO codes for the countries in each layer (in the EEZ shapefile, we used ISO_ter1 as ISO_ter2 and ISO_ter3 were only filled in in case multiple countries claimed or governed a particular territory)
 ![Input Layers](image1.png)
5. Make the resulting layer permanent in the layer overview, save it as GDP [year]
6. Open the attribute table of the resulting shapefile, sort by GDP so that all the NULL values come to the top of the table, then toggle editing, select all the 7. Entries with NULL values, and save the table. This creates a shapefile that includes only EEZs for countries that we have GDP data for
8. Create a graduated fill for GDP with five classes, set to Equal Count (Quantile)
9. Repeat this for all GDP attribute tables to create shapefiles of the EEZs that link our GDP data to the right countries


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

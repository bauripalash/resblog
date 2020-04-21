---
layout: post
title: Young People Most Infected from Coronavirus in India
categories:
- Coronavirus
description: > 
    In this project we are trying to figure out the age distribution of COVID-19 infected patients in India to understand the risk rate of other non infected people.
image: "/assets/imgs/ica-9-4.png"
author: Palash Bauri
modified_date : 2020-04-21

---

**Analysis by , Palash Bauri , on 9 April , 2020**

---

**Analysis Of Age Distribution among COVID-19 infected people in India.**

**Summary :**  

In this project we are trying to figure out the age distribution of COVID-19 infected patients in India to understand the risk rate of other non infected people.

The data we used for this analysis came from crowd sourced data sheet of covid19india.org. The data was in JSON format which was converted to CSV with a Python script I made [<sup>[1]</sup>](#1) . From there we used Matplotlib and Seaborn to plot the graph of Age distribution cross referenced with current status of the patients in that age bracket.

**Graph Result :**

![](https://i.imgur.com/UFfxjz6.png)

Notes : Only 16.6% (1065 out of 6417 People) of Patients' Age is known to us as of now.

**Analysis :** 

From the above graph we can see , Infection rate is high among young people , to be specific at the age bracket of 30 to 40 , 20 to 30 and so on , then 40 to 50 , 50 to 60 and 60 to 70 and so on. But the mortality rate in quite high in older age groups in comparison to younger age bracket,  and Recovery is quite distributed among all age brackets but to be more in-depth we can see that age bracket of 50 to 60 has high recovery rate, then 20 to 30 and so on.

Everything seems normal till now , but if we take a look at WHO reports, It is mentioned that Older people are most vulnerable but young people are not immune too [<sup>[2]</sup>](#2) but still its quite well understandable that younger people have strongest immune systems so they should be less effected in comparison to older people but we can clearly see that's not the case here.

To bust the mystery  , we have to scroll through news. We well see there a common picture , Young people are usually the ones to break the lock-down which was declared on 24th March and go out , sometime to buy daily commodities and sometimes for no reasons at all. That's why they become a easy target for Coronavirus infection.

**Conclusion :**

From the above analysis we can conclude that , younger people are mostly infected because they are the one who are more exposed to the SARS-CoV-2 aka. Coronavirus by breaking the nationwide lock-down for necessary and unnecessary reasons. To prevent that we must not go outside unless it is absolute necessity.

Stay Home. Stay Safe.

----
#### Footnotes

<a class="anchor" id="1">Python Script to Convert Crowdsourced JSON Data to CSV : </a> 

```python
import json
import pandas as pd
import sys
import requests 

COLS = {'agebracket': 'AGE', 'backupnotes': 'BACKUP NOTES', 'contractedfromwhichpatientsuspected': 'SUSPECTED INFECTION FROM PATIENT', 'currentstatus': 'STATUS', 'dateannounced': 'ANNOUNCED DATE', 'detectedcity': 'DETECTED CITY', 'detecteddistrict': 'DETECTED DISTRICT', 'detectedstate': 'DETECTED STATE', 'estimatedonsetdate': 'ESTIMATED ONSET DATE', 'gender': 'GENDER', 'nationality': 'NATIONALITY', 'notes': 'NOTES', 'patientnumber': 'PATIENT NUMBER', 'source1': 'SOURCE 1', 'source2': 'SOURCE 2', 'source3': 'SOURCE 3', 'statecode': 'STATE CODE', 'statepatientnumber': 'STATE PATIENT NUMBER', 'statuschangedate': 'STATUS CHANGE DATE', 'typeoftransmission': 'TYPE OF TRANSMISSION'}

RCOLS = ["PATIENT NUMBER" , "AGE" , "GENDER" , "STATUS", "ANNOUNCED DATE" , "TYPE OF TRANSMISSION" ,"DETECTED CITY" , "DETECTED DISTRICT" , "DETECTED STATE" , "STATE CODE" , "NATIONALITY" , "STATE PATIENT NUMBER" , "STATUS CHANGE DATE" , "SUSPECTED INFECTION FROM PATIENT" , "ESTIMATED ONSET DATE" , "SOURCE 1" , "SOURCE 2" , "SOURCE 3" , "NOTES" , "BACKUP NOTES"]

def main():
    j = "https://raw.githubusercontent.com/covid19india/api/master/raw_data.json"
    c = "data.csv"
    try:
        res = requests.get(j).json()["raw_data"]
        df = pd.read_json(json.dumps(res))
        df.rename(COLS , axis = 'columns' , inplace=True)
        df = df.reindex(columns=RCOLS)
        df.to_csv(c , index=False)
        print("DONE!")
    except Exception as e:
        print(e)
        print("FAILED")
    
main() 
```

#### References

<a class="anchor" id="2">[2] WHO Myth busters</a> : <https://www.who.int/emergencies/diseases/novel-coronavirus-2019/advice-for-public/myth-busters>

---

Sources : 	

- Data Sources : 
  - Ministry of Health and Family Welfare of India , <https://mohfw.gov.in>
  - Covid19India.org's Crowd sourced Data , <https://covid19india.org>

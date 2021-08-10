# How do Hazaras Report their Language and Culture at Census Time? 

Community activists ran a campaign in July and August 2021 to encourage Australian Hazaras to declare their language and identity in the 2021 Australian Census. Since Hazaras are a persecuted ethnic group in Afghanistan who have been denied legitimacy in that country for decades, community advocates argued that it is vital that Hazaras are recognised as a distinct group here in Australia, where many now live as refugees or former refugees. The campaign asked Hazaras to declare their ethnicity clearly by giving their language as Hazaraghi and their ancestry as Hazara. 

To provide clarity on how Hazaras had answered these questions in the previous census in 2016, and then to show what needs to change in 2021, I performed an analysis of a customised dataset and shared this with the community advocates. 

**Current state of population estimates:** Before getting started, I reviewed several reports and found large discrepancies in population estimates. An SBS news article claims that "Australia is now home to some 50,000 Hazaras, many of whom fled Afghanistan in the late 1990s and early 2000s when the Taliban first took power" (https://www.sbs.com.au/news/hazara-australians-fear-their-people-in-afghanistan-could-soon-be-massacred), while a missionary website states that there are 16,000 Hazaras (https://joshuaproject.net/people_groups/12076/AS). A regional report states that "(t)hrough this project, it was revealed to us that the 2016 Australian Census population estimates of 1,200 Afghanistan people living in the Murray PHN region are outdated. Community leaders believe that the population is over 3,000 people" (https://www.murrayphn.org.au/wp-content/uploads/2019/07/RP0060-Hazara-community-report_2019_V1_Summary_V1E.pdf). This fits with my analysis of the amount of under-reporting. The Australian government's Afghanistan-born Community Information Summary (https://web.archive.org/web/20200413223915/https://www.homeaffairs.gov.au/mca/files/2016-cis-afghanistan.PDF) is based on the 2016 Census data, however there are some flaws. One is that the Ancestry and Language sections only count Afghanistan-born people, which excludes displaced Afghanis born in other countries, such as Pakistan, or people who have been born in Australia but identify as having Hazara ancestry. In addition, the Ancestry and Language summaries are separate, whereas my analysis combines these two variables and then looks at where they do and do not intersect, which allows us to infer the total number of Hazaras. 

I am not permitted to upload ABS microdata to this repository so I have uploaded screenshots of the Tableau workbook. Unfortunately, this means that all interactive features of the charts and dashboards are lost, however this should at least illustrate the steps I undertook.

![location_Hazaraghi](https://user-images.githubusercontent.com/63942300/128850432-54a1325a-7665-4c33-a6aa-c30e03839a08.png)
*Fig 1 - I plotted Hazaraghi speakers by their local government area on the national map.*

**Data:** Data are from the ABS 2016 Census of Population and Housing - Counting Persons, Place of Usual Residence dataset. The dataset was downloaded using the Census TableBuilder, which makes all variables available for selection into custom tables using the ABS Table Builder Pro online tool (Australian Bureau of Statistics, 2021). The Census is a national demographic survey run every 5 years and managed by the ABS.

The data show people living in Australia at the time of the 2016 Census. Mutiple reports were created and then downloaded for these analyses: 
- people who speak Hazaraghi at home instead of English (LANP) by Local Government Area (LGA) and State
- people with Hazara ancestry (ANCP) and the language they speak at home (LANP)
- people who speak Hazaraghi (LANP) with their first ancestry (ANCP1) and second one (ANCP2)

**Variables:** 
- ANCP - Ancestry Multi Response: The two ancestry variables (ANC1P and ANC2P) are combined into one variable Ancestry Multi Response (ANCP). Ancestry is coded using the *Australian Standard Classification of Cultural and Ethnic Groups (ASCCEG), 2016.* All ANCP variables were analysed at the 4-digit level, which is the most detailed level of the classification.

- ANCP1 - Ancestry 1st Response

- ANCP2 - Ancestry 2nd Response 

- LANP - Language spoken at home. The filter used was 4107 - Hazaraghi, which is the most granular level of language in the *Australian Standard Classification of Languages (ASCL), 2016.*

- LGA - Local Government Area

- Total - Count of persons

The ABS states that: "To analyse ancestry, both ancestry variables (ANC1P and ANC2P) must be used. There are two ancestry variables because respondents to the Census are asked to report up to two ancestries in their response to the Census question on ancestry. Respondents do not have the option of ranking their answers to the ancestry question, so where a respondent reports two ancestries, those two ancestries have equal standing." (https://www.abs.gov.au/ausstats/abs@.nsf/Lookup/2901.0Chapter602016) 
After analysis, I deduced that that the ANCP counts were the sum of ANCP1 and ANCP2. There is some minor discrepancy in totals and I have queried this with the ABS. 

**Variable Types:** All variables are categorical nominal except for Total, which is numerical discrete.

### Analysis
![LGA_Hazaraghi](https://user-images.githubusercontent.com/63942300/128854382-1a019370-32f0-4d35-808f-fa310d0bfdc1.png)
*Fig 2 - Totals below 50 have been filtered out to prevent individuals and small groups from being identified*

![langs_Hazara](https://user-images.githubusercontent.com/63942300/128854774-a3230d83-2e02-41da-bb49-a23c2447dc87.png)
*Fig 3 - I took all people with Hazara ancestry (total = 16,051) and looked at which languages they speak.* 

![ancestry_Hazaraghi_not_combined](https://user-images.githubusercontent.com/63942300/128855112-dbb1fb90-e307-4b5d-a0d4-c71c18e688b2.png)
*Fig 4 - I then took all people who spoke Hazaraghi and looked at which ancestry or ancestries they selected. They can pick 1 or 2.*

I then used a cross-tabulated report of ANCP1 and ANCP2 and extracted the combinations of ancestries, to give a more nuanced picture of how people identify their ancestry. This was a manual and laborious process, but it gave a much greater level of detail than the combined ANCP variable. I cleaned the data by removing all counts of the Not applicable category of the ANCP variable, which refers to persons who provided a first ancestry but did not provide a second.  

![ancestry_Hazaraghi](https://user-images.githubusercontent.com/63942300/128855678-48608399-2eab-4c1d-959a-e63e19c7ae2b.png)
*Fig 5 - Combinations of ancestry show that the majority of Hazaragi speakers pick one ancestry only: Hazara or Afghan. The most  popular combination is Hazara and Afghan.* 

![ancestry_Hazaraghi_Pie](https://user-images.githubusercontent.com/63942300/128859279-2b077997-2217-45ef-8310-c457c08133f2.png)
![pie_legend](https://user-images.githubusercontent.com/63942300/128859290-4a988c3d-5305-4572-929a-43d8ac9cf3b9.PNG)

*Fig 6 - Here I started to bring the information on ethnicity and language together to show how consistently people had anwsered these two questions.* 

I then experimented with various dashboard presentations of this information and tested them with one of the Hazara community advocates. I decided in the end to create a simple infographic in Powerpoint to convey the current state and the potential for improvement. This has been shared on LinkedIn. 

### Conclusion
I am excited to see what the 2021 results will show for the Hazara community. Assuming that people do respond to the census and that they use the opportunity to identify their ethnicity through ancestry and language, there is the possibility for the numbers to double. 

![Hazara_infographic](https://user-images.githubusercontent.com/63942300/128857695-ead2dd2e-d084-4e57-8c23-4b10d9009a33.PNG)
*Fig 7 - Infographic showing that only 45% of people who could identify as Hazara and Hazaraghi speakers did so in 2016*





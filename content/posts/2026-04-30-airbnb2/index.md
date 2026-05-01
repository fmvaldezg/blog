---
title: "Should we regulate Airbnb? Part 2*"
date: 2026-04-27
draft: false
summary: "A brief analysis of Airbnb in Ecuador and some ideas for its regulation."
tags: ["GIS", "geography", "short-term retanls", "Airbnb"]
---

<small>*Translated from the [original post in spanish](https://blog.felipevaldez.com/es/posts/2026-04-30-airbnb2/).*</small>

In my previous post I shared some reflections on the regulation of short-term rentals in Ecuador. This time I will focus more on how to obtain and analyze the data that would enable efficient regulation of this type of activity. Before that, I would like to clarify some reasons why this activity should be regulated.
 
The report ["The Threat of Short-Term Rentals to Housing: A Critical Perspective on Airbnb's Global Expansion"](https://insideairbnb.com/reports/the-threat-of-short-term-rentals-to-housing-en.pdf), produced by [Inside Airbnb](https://insideairbnb.com/) and the Housing Justice Data Lab, details how short-term rental platforms have evolved from 'peer-to-peer rental' websites into systemic threats to housing stability worldwide. Analyzing data from more than 200 countries, the authors found that the prevalence of unhosted entire-home listings removes millions of units from the long-term residential market. Increasingly, there are commercial operators and non-local residents behind the listings. This drives up housing costs and worsens urban inequality, especially in the Global South. They also analyze how major international events and the lack of effective government regulation accelerate this phenomenon. As a result, they suggest developing strict policy tools, such as primary residence requirements and mandatory registration, to protect local communities from displacement[^1].
 
From this, we can extract 2 elements for data analysis:
 
1. The type of property listed: room vs. entire home
2. The type of advertiser: host vs. commercial
   
The first can be extracted directly from the Airbnb platform, which even offers it as a search filter. The second can be a bit more complicated to identify, since commercial advertisers may offer properties under different names or under the name of a company. This is precisely where registration with a government authority is fundamental, as it allows verification not only of the advertiser's authenticity but also of their relationship with the listed property.
 
Let's see an example of how to obtain and analyze the data. We will analyze the short-term rental landscape on Santa Cruz Island in Galápagos.
The Galápagos are a particular case study for three reasons. First, given their protected status as a National Park, they have many special regulations that seek to limit the number of residents and tourists on the islands. Second, the main economic activity for several decades has been tourism, which can undeniably be contradictory to conservation objectives. Third, being an island far from the mainland, many resources are scarce and expensive, including access to drinking water, electricity, and even food.
 
## Obtaining the data
 
Although the Airbnb API is not publicly available, there are some alternatives for extracting the data. The first is a series of external data providers such as [AirROI](https://www.airroi.com/) or [Apify](https://apify.com/api/airbnb-api). These two offer Airbnb data for a fee, although they also have some free data visualization options. The second option is to extract the data with open webscrapers[^2] using python or another programming language. For this, you can use pyairbnb or ScrapeBnB.
 
{{< alert >}}
Using a webscraper to extract Airbnb data violates their terms of service. However, depending on the use given to the data, it does not constitute an illegal activity.
{{< /alert >}}
 
## Trend analysis
 
According to AirROI data, in Puerto Ayora the supply of properties on Airbnb has fluctuated between 200 and 420 over the last 3 years. When performing a search on the Airbnb platform, the figure of properties available for 5 nights during the month of May 2026 is 421. The graph shows how the supply of properties has been increasing since July 2024, although it appears to have stabilized in the first months of 2026. This is particularly interesting because, starting in May 2025, the Ecuadorian Ministry of Tourism began enforcement activities in compliance with the Organic Law of Special Regime for the Province of Galápagos - LOREG. This law, in its article 72, prohibits the construction of new hotel infrastructure and, in its article 102, establishes sanctions for new constructions or expansions of existing infrastructure that do not comply with the provisions of the Hotel Regulation Plan (approved in June 2024). It would therefore be expected that, from that date on, the number of listings on Airbnb would decrease.
 
{{< figure src="img/trend.png" alt="AirROI screenshot" caption="Trend of Airbnb listings from May 2023 to March 2026 taken from AirROI, accessed on April 28, 2026" >}}
 
<div style="max-width: 400px; margin: 0 auto;">
{{< x user="minturgalapagos" id="1923478044527689776" >}}
</div>

This is one of the advantages of external data providers like AirROI: being able to consult a historical series and perform comparative calculations between listed properties and booked properties. In the following graph, for example, you can observe the evolution of total monthly revenue generated by properties by type. Seasonal variations can be observed with peaks in the months of June, July, and August. However, it is interesting to see how the total revenue for April 2025, after the regulations, is more than double the total revenue for the same month of the previous year.
 
{{< figure src="img/revenue.png" alt="AirROI screenshot" caption="Trend of total revenue by property type from May 2023 to March 2026 taken from AirROI, accessed on April 28, 2026" >}}
 
This means that although the total number of listings compared to the months prior to enforcement appears to have decreased (from 415 in July 2025 to 362 in March 2026), the revenue earned has been higher. That is, the apparent decrease in supply may have caused an increase in listing prices or in the actual number of properties rented per month. Let's remember that not all listed properties are rented; occupancy is around 20% for the month of April 2026.
 
## Property type analysis
 
Another interesting point for analysis, as I already mentioned, is the type of property being offered. AirROI data shows that in Santa Cruz, 60% of listings are for entire properties and 36% are for rooms. Although it cannot be assumed that the total of entire-property rentals is offered by commercial advertisers, this phenomenon can affect the housing supply in a general way, as the InsideAirbnb report argues.
 
<div style="max-width: 60%; margin: 0 auto;">
{{< figure src="img/types.png" alt="AirROI screenshot" caption="Proportion of listings by type of property offered on Airbnb from May 2023 to March 2026 taken from AirROI, accessed on April 28, 2026" >}}
</div>

Based on this, it can be assumed that due to the lack of regulation of this activity in Puerto Ayora, there are 239 dwellings that are not available to local residents on average between 2023 and 2026. According to the 2020 Census [^3], there are 5,888 private dwellings in Puerto Ayora. That is, Airbnb is occupying 4% of the dwellings in the parish.
 
Now, by performing a direct search on Airbnb for the first five nights of May 2026, we find that there are 855 properties available. Of these, 417 are entire-property rentals, representing 7% of the total housing stock.
 
<div style="max-width: 60%; margin: 0 auto;">
{{< figure src="img/types2.png" alt="AirROI screenshot" caption="Proportion of listings by type of property offered on Airbnb for the first days of April 2026" >}}
</div>

The number does not seem so overwhelming, but it must be considered that, if so, in Santa Cruz there is a pressure and capture of the housing supply by Airbnb similar to that identified in high-pressure and deep-saturation markets in Latin America, where more than 60% of listings are for entire properties for rent.
 
## Distribution of supply and deep saturation
 
"Deep saturation" refers to an extreme concentration of short-term rental listings at very small spatial scales, such as specific neighborhoods or blocks. This phenomenon becomes visible when data is analyzed at the local level, revealing areas where residential housing has been almost completely absorbed for tourism purposes. In some cities, a hyper-concentration of properties is evident in neighborhoods or zones of high tourist value. This, without doubt, can be an influencing factor in so-called 'touristification', which causes the displacement and exclusion of the local population from these areas.
 
To identify this saturation, it is necessary to analyze the location of listed properties and, consequently, the data needs to contain this information. The sources or methods for extracting data presented earlier make it possible to visualize the location of the properties because they contain their coordinates.
 
In the following map you can see how, in the case of Puerto Ayora, there is a notable concentration of listings, especially of entire properties for rent, concentrated towards the bay area, since this is the zone most attractive to tourism due to its proximity to the sea, the dock, and the shops. This map was built with data extracted directly from Airbnb by querying properties available for the first five days of April 2026. The map is interactive and allows filtering the view by property type; in the left-hand window it shows the total of properties by type, the price range per night, and the rating from previous guests. Tools like these, which allow not only visualizing the phenomenon but also monitoring it over time, are essential for the formulation and application of efficient regulatory policies. One can build on a tool of this type by adding, for example, rental housing prices on the island, infrastructure, socio-demographic structure, among others.
 
{{< carousel images="{img/heatmap.png,img/entirehome.png,img/hotspots.png,img/clusters.png}" aspectRatio="9-8" captions="{img/heatmap.png:Heatmap of listings,img/entirehome.png:Location of entire-property listings,img/hotspots.png:Hot and cold spots of prices,img/clusters.png:Clusters of listing concentration}" interval="1500">}}
 
<br></br>
 
You can see an interactive version of the map here.
 
 
{{< button href="https://fmvaldezg.codeberg.page/ptoayora-abb2026/" target="_blank" >}}
View map
{{< /button >}}
 
## Conclusions
 
In the two previous posts I have tried to show the usefulness of using data to inform regulatory policies for short-stay rentals. So, should Airbnb be regulated? An activity of this type definitely should be regulated since, although it may be presented as an opportunity to supplement the income of the local population, there is sufficient evidence that, being so lucrative, it ends up being captured by large capital. Thus, in the medium and long term, the lack of regulation of this activity may end up being much more harmful to the local population than what its enforcement now appears to be.
 
That said, it is very important that regulation seriously aims to protect the well-being of the great majority, for example by preventing increases in rental prices or the uncontrolled growth in the number of visitors. For this reason, this regulation must, on the one hand, respond to the specific analysis of the phenomenon at the local level and, on the other hand, must be complemented by other regulatory policies on other spatial aspects such as urban land enablement, construction control, projection of basic services, among others.
 
The Galápagos case is very particular since, being an island with many regulations regarding residency and tourism, the existence of short-stay rentals could indeed function as an opportunity to supplement the income of local inhabitants. At the same time, the regulation of the activity may end up benefiting only a few, especially commercial advertisers. It is important to consider that Galápagos already has regulations that seek to control the number of tourists; however, this number increases every year. On the other hand, the lack of regulation of these activities will not reduce the existing inequalities in the archipelago, as some 'hosts' would like to make it appear.
 
## References
 
[^1]: [Cruvinel, A., & Cox, M. (2026, March). The Threat of Short-Term Rentals to Housing: A Critical Perspective on Airbnb's Global Expansion. Housing Justice Data Lab / Inside Airbnb.](https://insideairbnb.com/reports/the-threat-of-short-term-rentals-to-housing-en.pdf)
 
[^2]: [Zhou, J. (2026, February 2). Is it legal to scrape Airbnb data?. AirROI. https://www.airroi.com/blog/is-it-legal-to-scrape-airbnb-data](https://www.airroi.com/blog/is-it-legal-to-scrape-airbnb-data).
 
[^3]: INEC, VIII Population and VII Housing Census 2022.
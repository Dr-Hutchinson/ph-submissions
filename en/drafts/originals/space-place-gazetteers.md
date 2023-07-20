---
title: "Working with Named Places: How and Why to Build a Gazetteer"
slug: space-place-gazetteers  
layout: lesson 
collection: lessons
date: YYYY-MM-DD
authors:
- Susan Grunewald
- Ruth Mostern
reviewers:
- Forename Surname
- Forename Surname
editors:
- Yann Ryan
review-ticket: https://github.com/programminghistorian/ph-submissions/issues/XXX
difficulty: 
activity: 
topics: 
abstract: Short abstract of this lesson
avatar_alt: Visual description of lesson image
doi: XX.XXXXX/phen0000
---

{% include toc.html %}

# 1. Lesson Overview

This lesson introduces readers to gazetteers, which are spatial knowledge organization systems about places that record names, spatial footprints, and other characteristics that have historically been associated with any locale. The lesson will explain how to think about the concept of place, why gazetteers are useful for spatial history, how to use historical information to create a gazetteer, and how to enhance and share a gazetteer.

A well-structured gazetteer reflects the fact that places are conceptual entities, not simply names or points on maps. Any given place may have had multiple names in numerous languages over the course of history, potentially involving conflicts about who has the power to enforce any of those names. The spatial extents, names, and feature types (settlements, buildings, nations, mountains, and so on) of places frequently change over time. Gazetteers are essential resources for spatial history. Unlike maps, gazetteers can readily connect named spatial entities with one another and with modern locations, and gazetteers make it easy to annotate any identified place with information about any texts, events, people, or other places that have been associated with it.

This lesson will demonstrate how to build gazetteers, starting with simple spreadsheets and then building them into linked open data resources to share with other projects.

At the end of this lesson, learners will be able to:

a. Define what a gazetteer is, understand the concept of place, and distinguish gazetteers from other forms of spatial information.
b. Identify scenarios for which creating a gazetteer may be preferable to using a geographic information system.
c. Transform a historical text into a gazetteer.
d. Share a gazetteer with other platforms to enhance it and use it for analytical purposes.

# 2. Historical Example

This lesson will show how to create a gazetteer based on the online [Itinerary of Benjamin of Tudela](https://depts.washington.edu/silkroad/texts/tudela.html), an English translation of a Hebrew-language itinerary composed by Benjamin of Tudela (1130-1173), a Jewish traveler who journeyed between the Iberian Peninsula and West Asia in the twelfth century. Benjamin transited through three hundred cities along his route, recording information about geography, ethnography, commerce, Jewish life, and Jewish-Muslim relations.[^1] This text is a major work of medieval geography and Jewish history. Those following the lesson will build a gazetteer of places that Benjamin visited. This example will teach learners to extract place names from written historical texts and use them to build a succinct gazetteer. The waypoints along Benjamin’s journey are cities with synagogues, so the lesson will explain how to build a gazetteer that includes historic place names as well as other feature types that are important in the historical record. This fulfills two lesson components: first, why and how a scholar might choose to build a basic gazetteer, and second, how a gazetteer can support historical analysis.

# 3. Space, Place, Gazetteers, and Knowledge Organization Systems

What is a place? You might think that a place is simply a geographic location, but it is more helpful to think of a place as a concept. The geographer John Agnew has postulated that when we say something is a place, we are talking about three different ideas. First, any place has a specific *location*. It lies somewhere on the surface of the earth. Second, the place is a setting for social relations. A place is a *locale* that shapes values, attitudes, or behaviors. Any workplace, school, or prison is a locale. Finally, any given place evokes a unique *sense of place* for each of its denizens, evoking specific impressions and sensations of belonging or unbelonging. That is to say, a place is a location where memorable events have transpired.[^2]  Cultural geographers tend to distinguish the concept of place, with its references to unique and distinctive settings for human activity, from that of space, which refers to the totality of all possible geographical expanses, many of which may exist regardless of whether they are sites of human meaning.  

Many theorists of place describe the concept in historical and temporally dynamic terms.  The Marxist feminist geographer Doreen Massey defines places as sites of “meeting up of history in space,” where people with different relations to authority and security encounter one another.[^3] The anthropologist Tim Ingold emphasizes the fact that “places do not just have locations but histories,” because they are networks of habitation where people’s pathways become entangled.[^4] The Black activist geographer Ruth Wilson Gilmore underscores the fact that struggles for social justice are always spatial, and thus they are always about processes of placemaking.[^5] For these scholars, place can never be distinguished from travel, activity, relations of power, and human interaction. With its focus on human activity, meaning, contestation, and change over time, place - the purview of names, lists, descriptions, and gazetteers - is often a more meaningful concept for spatial historians than space – the domain of maps, which cannot easily represent human interaction and meaning.  Place is an essential concept for many types of historical analysis and data management.

The set of values, institutions, and relationships associated with any given locale are multitudinous, dynamic and unstable. A place may change substantially in all its particulars even as it persists as a spatial entity. Names for places may coexist, or they may succeed each other after regime changes or major events. Constantinople (also known historically as Lygos, Byzantium, Nova Roma, Rūmiyyat al-Kubra, and other monikers) also took on the name Istanbul after the Ottoman conquest in the fifteenth century, though both names were used officially until 1928. When Dutch settlers colonized the “hilly island” that Lenape residents called Manahatta, they named their settlement Neuwe Amsterdam, which became New York in 1664 after the English took over the Dutch colony. Informally, people might also refer to the city by the 1807 term Gotham or the 1921 term Big Apple. If they are speaking or writing in Chinese, they would call it Niuyue (纽约).

Conversely, places may retain stable names even as their spatial footprints change, for instance when rivers break their banks and take new courses, or when metropolitan areas expand their boundaries. Even as the mappable extent of a river may change over time, the river persists as a fixed conceptual entity in the minds of the people who navigate it, live around it, or read and write about it.  The Yellow River is still the Yellow River even when it is dry, dammed, or flooded.  From the perspective of knowledge modeling in a gazetteer database, the river is a single entity that is associated with a large cluster of attestations specific to certain events and time periods.

**The first task for anybody embarking on a digital spatial history project is to decide whether to begin with a dataset-based gazetteer, or a map-based geographic information system.**  A project emphasizing the conflicting, contested, and dynamic characteristics of places, as well as spatial information reflected in textual attestations, should begin with a gazetteer.  A GIS is only the logical starting point for a spatial history project centered on geography and spatial relations *per se*.

Indeed, although geometry is necessary for making maps, the symbols on maps only tell a small part of the story of a place. The way to model rich and multivocal data about place making events, contestation and power, places as settings for social events, and to represent the sense of place, is with a gazetteer, not a map. Gazetteers are excellent for collecting information such as what a place has been called, by whom, why, and when; who has been there; what has occurred there; who has contended for authority over it; or what texts have referred to it. These are all questions that are of special interest to historians. Not every spatial project requires a map. In many cases, a gazetteer is a more useful way of capturing and analyzing historical spatial information.

In its simplest form, a gazetteer is an index or dictionary of place names. Gazetteers do not need to include geographic coordinates, though many do so to enable visualization of spatial data. Gazetteers often include a controlled vocabulary of information about feature types that describe places as well: whether a place is a settlement, a waypoint on a travel itinerary, or a geographical feature such as a mountain or river. A gazetteer, especially a historical one, is a kind of knowledge organization system (KOS). A KOS is a tool “that brings together related concepts and their names in a meaningful way, such that users of the KOS can easily comprehend the relationships represented.”[^6] Historical gazetteers link discourses about a place or places over time. The shape and organization of the KOS is determined by the shared characteristics of the places that need to be modeled.

Based on the above discussion, it should be clear that **the most important consideration when constructing a gazetteer is to recognize that place is the fundamental entity in any well-designed gazetteer**: not each individual place name, and not each attestation of the existence of a place at a certain date in a particular source document.  

The author of a historical gazetteer that includes information about the great metropolis situated at the mouth of the Hudson River would do well to group information about its many names into one complex entity associated with a single ID number: Lenape Manahatta, Dutch Neuwe Amsterdam, British colonial New York, and Washington Irving’s 1807 coinage of Gotham.  Grouping multiple names and attestations into a single gazetteer record allows for several affordances.  First, it makes the gazetteer into a powerful thesaurus. Second, it makes it possible to map as much information as possible onto a single geographical referent. Third, it makes the gazetteer into a compelling and potentially decolonial work of history which, by collecting names and attestations together, tells a story of sovereignty, colonialism, and culture.  Finally, it improves search and discovery, especially in the context of linked open data.

To be sure, it is a matter of personal and scholarly judgement and of research strategy to decide whether these names do indeed refer to a single place.  After all, Manahatta was the name of an island, not an inhabited place, and that island today is the site of only one of the five boroughs of New York City. There is no objective way to decide whether to group these names together as references to a single place. In an ambiguous case like this, the consideration is simply whether one’s own research and visualization tasks would be enhanced more effectively by grouping these names together, or by leaving some of them separate and potentially specified as “relations” using the [GeoJSON-LD Linked Places format](https://github.com/LinkedPasts/linked-places-format) or another similar data format. Names and attestations that are grouped into a single entity are easiest to find and use together, but the decision to group disparate pieces of information together may come at the expense of precision, accuracy and nuance. Beyond human judgement, these questions are the domain of entity resolution, an open and unresolved topic in information science, natural language processing, and geoscience.[^7]

In a widely cited 2006 book, the geospatial librarian Linda Hill suggested that each entry in a well-structured gazetteer should include at least one name, at least one set of coordinates, and one or more feature types.[^8] For historians, it is often especially important to include modern place names if the name has changed, as well as a temporal range for when the older name was attested in a source. For those operating with multilingual sources or projects, it may also be important to note different names or transliterations for a given place, for example, Moscow (EN), Moskau (DE), Moscou (FR), Москва (RU). The [Linked Places GeoJSON Format](https://whgazetteer.org/tutorials/choosing/) and its delimited file derivative LP-TSV are widely used historical gazetteer data standards. The next section provides a hands-on example of how to model and build an LP-TSV compatible gazetteer from a historical text.  

# 4. Building a Gazetteer from a Historical Text

Historians often work with detailed written texts such as memoirs or travelogues that may contain a wealth of spatial information. *The Itinerary of Benjamin of Tudela* is one such example of rich, descriptive historical text that can be mined for data for spatial research.

Benjamin of Tudela was a twelfth century Spanish Jewish traveler whose text describes his expedition and his interactions with different Jewish communities. A spatial historian interested in this text may want to discover where Benjamin of Tudela travelled on his grand journey, and how he interacted with Jewish communities in the locations he visited. These questions suggest the outline for a gazetteer spreadsheet. The authors of this tutorial recommend using either Microsoft Excel or Google Sheets for the process of creating a simple gazetteer that is compatible with the LP-TSV format.

To begin, navigate to the section entitled “THE ITINERARY OF BENJAMIN OF TUDELA” on the [web version of this text](https://depts.washington.edu/silkroad/texts/tudela.html#N_3_).

{% include figure.html filename="or-en-space-place-gazetteers-01.JPG" alt="Visual description of figure image" caption="Figure 1. The Itinerary of Benajamin of Tudela" %}

Open Excel or whichever program is your preferred spreadsheet software. From the first paragraph of *The Itinerary*, we know that we need a column of place names that are travel stops. In keeping with good practices for making spreadsheets that may need to be shared or exported into other software, we will also include an ID number column. The next section of this tutorial, on Linked Open Data, will explain why it is also a gazetteer best practice to include a place type to describe the travel stops. For now, we will assume that all travel stops are some kind of inhabited place.

You can use whatever column headers you want for your own research, but we are using ones based on the [Linked Places format](https://github.com/LinkedPasts/linked-places-format/blob/main/tsv_0.4.md) for the ease of future data interoperability. Using a standard from the start might be cumbersome at first, but it will save you lots of time later if you wish to share this project in a variety of ways.  

Inhabited place is a good choice because it is a standardized vocabulary term from the [Getty Art and Architecture Thesaurus](https://www.getty.edu/research/tools/vocabularies/aat/about.html), which is a structured resource that aims to improve access to information for art, architecture, and material cultural. It is also extremely useful for history projects as it is a well-established, controlled vocabulary that is used by a variety of different scholars and projects across a multitude of humanistic and social science disciplines. Using an established standard like this means that the data we create in this tutorial, or that you create for your own research informed by this tutorial, can be shared with other likeminded researchers to create new knowledge. We will thus also include a column for aat_type and use the aat code for [inhabited place, 300008347](https://www.getty.edu/vow/AATFullDisplay?find=300008347&logic=AND&note=&english=N&prev_page=1&subjectid=300008347), in this column.

As our second research question ties into questions of Jewish history, we will add a column for whether there is a Jewish population in the place and an additional column that includes further information about the description of the Jewish population. For simplicity’s sake, and for ease of future data sorting, we will write Y or NA (“not applicable” rather than “no,” since we don’t want to propagate false information about whether there was definitively a Jewish population based on this account) under the Jewish population column.

Please add two other columns as well.  In a Source column, record that your information comes from *The Itinerary*.  You can abbreviate the name of the source as you wish and maintain the full citation in a separate data dictionary document. For now, we will write, “ItineraryTudela” to make it easy to understand whose itinerary we are referencing. It is essential for digital spatial history projects like this to rigorously maintain the same standards of citation that would be expected from any other work of historical scholarship.  Recording this information in the spreadsheet itself rather than in metadata external to it makes it easy to add records from other sources if you expand your research in the future.

In an AttestedDate column, add information about the year for which you deem the information you are recorded to be correct.  Benjamin set out on his journey around 1165. It is not clear exactly when he composed *The Itinerary*, though we know that he died in 1173, and *The Itinerary* does not record the specific dates when Benjamin sojourned in each place he visited.  We recommend that you choose an arbitrary date of 1170, with a note in your data dictionary and your metadata indicating that this is an estimate.  

It is sometimes possible to ascribe precise starting and ending dates to specific elements in a gazetteer (such as the dates during which a certain place name was in official usage, or the dates during which a place held a particular administrative status, or during which a river followed a precise course).  More often, when we build gazetteers from specific historical sources, all we know is that the author of that source records the existence of a place at a given time: the existence of the place is attested in a source.  Over time, in a linked open data resource like the World Historical Gazetteer, which indexes multiple gazetteers together, it is possible to build up multiple attestations into a history of a place.  

The full Linked Places format makes it possible to add temporal information to every aspect of a complex gazetteer record. Multiple names, locations, and feature types associated with a given record can each include start dates, end dates, and attested dates.  For a simple spreadsheet like the one you are making in this exercise, it is cumbersome to include extensive temporal information.

It is always a good idea to include some form of temporal information in a gazetteer, and the LP-TSV format requires that you include at least one date.  If you find that you have no relevant temporal information to record, you can use -9999, which is the oldest possible year that many database systems can parse.

For now, your spreadsheet should look something like the screenshot below.

{% include figure.html filename="or-en-space-place-gazetteers-02.JPG" alt="Visual description of figure image" caption="Figure 2. Spreadsheet Template" %}

As a note, we are formatting our column headers in this way for future ease of data interoperability. If we were to export our data to mapping software like QGIS or ArcGIS, we need the ID column. Mapping software also does not like long column headers. ArcGIS, for example, can crash if a column header includes any spaces or is longer than 15 characters. Try to think of the shortest way of naming columns that make sense to you and potential future collaborators. Other important notes for spreadsheets and data interoperability include not using commas anywhere. Many programs that could use the spreadsheet for future analysis require that the spreadsheet be uploaded in .CSV or comma separated value format. This means that anytime the software sees a comma, it reads it as the boundary of a cell or row in the spreadsheet. Inserting commas will break the software and make the sheet unreadable. If you need a way to parse information, use a semi-colon. Also avoid most special characters if you can. They can also break the software. If you need to put a space in a column header, use an underscore.

You may wish to make a data dictionary as a separate document to store information about your abbreviations and other data management decisions for your and others’ reference. Including short descriptions of why your specific columns are important make your research a more valuable contribution to linked scholarly projects such as the World Historical Gazetteer. Other researchers will be able to then understand your editorial choices for data management and can better cite and make use of your data in their projects. Adding fuller descriptions in your data dictionary will also make it easier to extend your gazetteer in the future. The ability to continue to expand your project as well as to share it with others is another justification for citing your sources and including the historical information of when they were written. You might only use one source at the moment, such as *The Itinerary*, but in the future you might add other travel accounts to the gazetteer and it is important to be able to parse out who used which name variant and when.

Now we are going to start filling in our spreadsheet with the information from the first paragraph. By building this out for the first paragraph, we can see if our model works well or needs to be changed in any way. It’s better to test with a smaller sample of data and tweak earlier rather than later.  If you follow the model we outlined, your spreadsheet should look something like the image below.

{% include figure.html filename="or-en-space-place-gazetteers-03.JPG" alt="Visual description of figure image" caption="Figure 3. Initial Stage Spreadsheet with data from textual source" %}

We can see quickly that Benjamin has described a wide variety of different types of information related to the Jewish community in three different settlements. An additional benefit of a gazetteer project is that it is highly iterative. An initial research question or two about the source led to its initial structure. Recording simple amounts of initial data can serve to generate follow-up research questions. In this case, a researcher might now want to know much more than just which settlements had some sort of Jewish population. There could be questions about the size of the populations in various settlements. In the case of Narbonne, Benjamin gives a figure of 300 Jews. In the cases of Barcelona and Gerona, no population statistics are given, but he describes either a “holy” or “small” congregation, which gives clues to the size of the Jewish population in the community. A researcher could then ask questions about which cities had Jewish populations, then which cities had large populations versus small populations. Additionally, researchers could see whether certain cities are centers of Jewish education, and so forth. The gazetteer has already generated a wealth of important information and subsequent questions. A researcher might wish to then create different columns for the different types of information about the Jewish population (i.e., congregation size, educational facilities, number of Rabbis listed, etc.). To make this data easier to filter and analyze later.

The second paragraph of the travelogue clues us into another important column: name variants. Benjamin mentions a settlement called “Har Gaash,” which he notes has an alternative name of “Montpellier.” We should record both names as other sources might list one name or the other and this gazetteer can then serve as a means to reconcile these two names around the same physical location. Insert a column after “TravelStop” and call it “AltName” to record any additional names given for a place. Then, continue processing the itinerary through the fourth paragraph for now. That will provide sufficient information for the remaining steps of this lesson. If you do not wish to continue making the spreadsheet, you can download a final version of the information through the first four paragraphs here. **NOTE - LINK TO FILE TudelaGazetteer, have it for download in the project repository**

{% include figure.html filename="or-en-space-place-gazetteers-04.JPG" alt="Visual description of figure image" caption="Figure 4. Spreadsheet with alternative names and additional information about the locations" %}

We could continue to build this gazetteer out for the rest of the text, and we would probably generate more research questions and data points to analyze. Even with what we have processed so far, we have information about Jewish history in the 12th century that is now connected to space and place. Those who compile data such as this might also want to map the data. This then brings one of the greatest challenges of historical-spatial research, taking historic names and mapping them with modern software. Major mapping software providers like Google Maps tend to have major name changes saved in their software, such as Stalingrad/Volgograd or Bombay/Mumbai, but these programs often lack more obscure historic names. With respect to our dataset, Tudela is there because the name has not changed. Google Maps also knows that Saragossa is an alternative spelling for Zaragoza, which is how the name appears on the map. Without Google doing this reconciliation for us, we might not know this to be the same place. Thus, we need to add new columns into our spreadsheet, one for modern names, and ones for latitude and longitude, to make mapping this information easier.

We also should add a column for the ISO code for the modern country where this location exists. It’s generally easiest to use the two letter ISO code. While many of these place names may be unique, Barcelona and Montpellier are not. Moreover, as this is a travelogue of a journey from Spain to Jerusalem, we know that our traveler will be traversing the lands of what became numerous modern countries. We may wish to ask research questions about that information and it is better to log the information consistently as we go along. Here is what the columns should look like.

{% include figure.html filename="or-en-space-place-gazetteers-05.JPG" alt="Visual description of figure image" caption="Figure 5. Spreadsheet with space for geographic information" %}

Where do we go to get the information about modern names for the places? There are a multitude of options for this work, but the easiest to use is the [World Historical Gazetteer (WHG) website](https://whgazetteer.org), a project which works to reconcile as many historic place names as possible around the globe with modern ones across a multitude of languages and alphabets. Navigate to the website and press the “Explore open access, historical place data” button to be taken to a search window.

{% include figure.html filename="or-en-space-place-gazetteers-06.JPG" alt="Visual description of figure image" caption="Figure 6. World Historical Gazetteer Navigation" %}

With the search interface now activated, let’s start with our first location, Tudela. The WHG gives us a few options. We know that Benjamin of Tudela is a Spanish traveler, so the second option of Tudela in ES for Spain is the one we want. We will click on this record to get a new window to open.

{% include figure.html filename="or-en-space-place-gazetteers-07.JPG" alt="Visual description of figure image" caption="Figure 7. World Historical Gazetteer search results for Tudela" %}

On the new page for Tudela, we can see that there are no other variants. The city is thus still called Tudela. We can also verify this with a Google Maps search. But the WHG will also give us the geometry for the city as well as the country code for the purposes of filling out our spreadsheet. The first search page gave the country code. On the page for Tudela, there is a green dot on the map showing its location. If we click on that dot, a new popup will appear that gives the latitude and longitude. We can copy and paste those into our spreadsheet.

{% include figure.html filename="or-en-space-place-gazetteers-08.JPG" alt="Visual description of figure image" caption="Figure 8. Tudela record in World Historical Gazetteer" %}

If we search the next record, Saragossa, we then learn that the modern name is Zaragoza. Again, we can capture the country code and latitude and longitude information from the WHG. If you follow these steps for the rest of the sample cities, your spreadsheet should look as follows. You can also download the filled-out spreadsheet here. **NOTE INCLUDE LINK TO FILE TudelaGazetteerModernNames FOR DOWNLOAD IN REPOSITORY**

{% include figure.html filename="or-en-space-place-gazetteers-09.JPG" alt="Visual description of figure image" caption="Figure 9. Completed spreadsheet for first paragarph of Benjamin of Tudela's travel itinerary" %}

Now that we have found the modern equivalents, we can conduct additional research. For example, do these places still exist? Has their identity changed over time? Do Jewish populations in these settlements remain? Have they grown?

# 5. Enhancing Gazetteers with Linked Open Data or Geographic Information System (GIS) Mapping

Simple gazetteers collect basic information about the names, feature types, and locations of places and their attestation in historical texts. They can be further annotated and enriched, as we started to do with the rich descriptive text about the Jewish populations in given settlements, and they can be linked with one another, as we did when we linked historic names with modern names and geometries.

Moreover, we can enhance the gazetteer that we have made about Tudela’s travels with larger collections of linked spatial data to ask new questions and find new answers such as additional content about medieval Jewish history. The best way to put our research into conversation with others and to harness the power of other analytical tools is to use Linked Open Data standards. Linked Data is structured data that can be interlinked with other data to undertake large queries. Linked Open Data is Linked Data that is released under an open license, meaning that it can be reused for other projects. You can find out more about Linked Open Data in [this *Programming Historian* Tutorial](https://programminghistorian.org/en/lessons/intro-to-linked-data).

We already used the World Historical Gazetteer to search for historic place names and to find coordinates for our spreadsheet. We could have used the data standards of the WHG to take our earlier spreadsheet and upload it into the WHG to make a map of our places and download an augmented spreadsheet with the geographic data. More information on how to do that can be found in [another *Programming Historian* Tutorial](https://programminghistorian.org/en/lessons/finding-places-world-historical-gazetteer). You can publish datasets through the WHG and reconcile your datasets against Wikidata and against the WHG index. This permits you to enhance the WHG datastore, and it also allows you to collect information that the WHG already knows about your target places. WHG place records are concatenations that link attestations about places from multiple gazetteers. This is a good way to manage the fact that no single gazetteer can contain all relevant information about a given place.
You can also annotate places indexed in the WHG to create Collections, which you can read more about [on the WHG website](https://whgazetteer.org/tutorials/collections/). This allows you to record complex information about places, to link places to one another based on a theme of your choosing, and to drive traffic from the WHG to any website you identify.

Once you have geographic information, you can also make a variety of maps with desktop or web-based geographic information system (GIS) software. QGIS is the open-source desktop software, and you can get started with it using [this *Programming Historian* tutorial](https://programminghistorian.org/en/lessons/qgis-layers).  

# 6. Conclusion

Recent scholarship has emphasized that the field of spatial history is not synonymous with the domain of historical GIS.[^9] Indeed, the intellectual history of spatial representation reflects the fact that maps have not often been widely used tools for recording information about the geographical settings for human activity.[^10] Today, when we use navigation apps to find directions to destinations, we are interacting with gazetteers, not reading maps. Despite these insights, education for spatial history tends to focus almost exclusively on GIS training.  

One purpose of this lesson has been to demonstrate why GIS may not be the best starting point for many spatial history projects, and to explain why you may want to begin with a gazetteer instead.  In that spirit, we conclude with a checklist that may assist in determining the strategy that will work best for your project and your research objectives.  

- Does your project include a corpus of places that have names, feature types, and locations?  In that case, you are well on your way toward building a gazetteer.  
- Do you want to track complex non-spatial information about places, such as multiple names, events that have occurred at them, attributes associated with them, texts that refer to them, or rich narrative information about them?  If so, a gazetteer is preferable to a GIS.
- Is temporal resolution important to your project?  In a GIS, temporal information can be effectively represented only with time stamped layers. In turn, that may force you to combine temporal references that you would prefer to keep disaggregated or to redundantly record information in multiple attribute tables.  A gazetteer may be preferable in such cases.
- Do you intend to publish place information in a linked data domain that permits you to combine it with other people’s contributions? If so, you should create a gazetteer.
- Does your project involve geospatially complex information and complex spatial analysis (such as geostatistical analysis, spatial autocorrelation, or spatial clustering)?  If so, you need to use GIS.
- Conversely, is the geospatial character of your data simple, or is spatial precision unimportant for your project?  If you are working with point locations rather than polylines or polygons, a gazetteer may be adequate.

Finally, remember that gazetteers and GIS systems can be readily transformed into one another once you understand the principles of place and gazetteer design that we have presented here. Named place information incorporated into GIS data can be exported and used as the basis for a more temporally and toponymically complex gazetteer; and equally, a gazetteer that includes geospatial coordinates can be imported into a GIS to facilitate spatial visualization and spatial analysis.

# 7. Related *Programming Historian* Lessons for Future Study

In addition to the related *Programming Historian* tutorials listed in Section 5 of this tutorial, readers might find some additional tutorials of use. Once you have a gazetteer, you can also use it for text analysis projects. You can run your list of names through a corpus or corpora to automatically find attestations of those same locations in other sources. An example of this would be to compare the locations named in Benjamin of Tudela’s travels with other contemporary travelogues to see which locations were seen as important for medieval travels. These two Programming Historian articles will run you through [using gazetteers for text analysis to extract keywords](https://programminghistorian.org/en/lessons/extracting-keywords) as well as [using gazetteers for text analysis and then mapping with the WHG](https://programminghistorian.org/en/lessons/finding-places-world-historical-gazetteer). Readers might also find the steps in the [Geoparsing English-Language Text article](https://programminghistorian.org/en/lessons/geoparsing-text-with-edinburgh) useful if they merely need a list of names listed in a text without additional attribute data.

In addition to using either QGIS or the WHG to map the data produced in this lesson, readers might also be interested in learning how [R can be used for geospatial data and historical research](https://programminghistorian.org/en/lessons/geospatial-data-analysis).

# Endnotes
[^1]: The standard English translation, which is the one used for the link we have included in this lesson is Marcus Nathan Adler, The Itinerary of Benjamin of Tudela: Critical Text, Translation and Commentary (New York: Phillip Feldheim, Inc., 1907).  [A scholarly trilingual (English, Hebrew, Arabic) version of the Itinerary](https://teipublisher.info/exist/apps/TraveLab/Benjamin%20of%20Tudela.xml)) was recently published. The English text on that site is the Adler version.
[^2]: John Agnew, “Space and Place,” in John A. Agnew and David N. Livingstone (eds.) *Sage Handbook of Geographical Knowledge* (London: Sage Publications, 2011).
[^3]: Doreen Massey, *For Space* (London: Sage Publications, 2005).
[^4]: Tim Ingold, *Lines: A Brief History* (Routledge, 2016), 105-6.
[^5]: Ruth Wilson Gilmore, “Fatal Couplings of Power and Difference: Notes on Racism and Geography” in Ruth Wilson Gilmore, Brenna Bhanda and Alberto Toscano, *Abolition Geography* (Verso, 2022).
[^6]: Ryan Shaw, “Gazetteers Enriched: A Conceptual Basis for Linking Gazetteers with Other Kinds of Information,” in *Placing Names: Enriching an Integrating Gazetteers*, ed. Merrick Lex Berman, Ruth Mostern, and Humphrey Southall (Bloomington: Indiana University Press, 2016), 52.
[^7]: Pasquale Balsebre, Gao Cong, Dezhong Yao, Zhen Hai, “Geospatial Entity Resolution,” *Proceeedings of the ACM Web Conference 2022* (2022), 3061-71 [https://doi.org/10.1145/3485447.3512026](https://doi.org/10.1145/3485447.3512026)
[^8]: Linda Hill, *Georeferencing: The Geographic Associations of Information* (MIT Press, 2006).
[^9]: For example Ian Gregory and Alistair Geddes, *Toward Spatial Humanities: Historical GIS and Spatial History* (Bloomington: Indiana University Press, 2014).
[^10]: Michael Curry, “Toward a Geography of a World Without Maps: Lessons from Ptolemy and Postal Codes,” Annals of the Association of American Geographers 95.3 (2005), 680-691. [https://doi.org/10.1111/j.1467-8306.2005.00481.x](https://doi.org/10.1111/j.1467-8306.2005.00481.x)
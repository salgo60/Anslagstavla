[![DOI](https://zenodo.org/badge/532209890.svg)](https://zenodo.org/doi/10.5281/zenodo.11183750)
* [Nationell dataverkstad skuggbacklog](https://github.com/salgo60/Anslagstavla/issues/3)
* jmf 
  * [Riksdagens öppna data](https://github.com/salgo60/Wikidata_riksdagen-corpus/issues/50)
  * [DIGG](https://github.com/salgo60/DiggUptime/issues/47)

# Anslagstavla
[Nationell dataverkstaden](https://www.vgregion.se/ov/dataverkstad/) försöker nu implementera en bättre lösning för kommuners Anslagstavlor. Just nu finns delar av detta uppdrag hos Metasolution....

Om [nationell dataverkstaden](https://www.vgregion.se/ov/dataverkstad) / [IA 20220930](https://web.archive.org/web/20220930120504/https://www.vgregion.se/ov/dataverkstad)

<img width="629" alt="image" src="https://user-images.githubusercontent.com/14206509/193143626-135d51d0-20f7-4e13-adef-42e6980bb357.png">

Eftersom [290 kommuner berörs](https://sweopendata.wikibase.cloud/query/embed.html#%23%23title%3A%20Kommuners%20Anslagstavla%20-%20test%20Wikibase%0A%23defaultView%3AMap%7B%22hide%22%3A%5B%22%3Fcoord%22%5D%7D%0A%0APREFIX%20wb%3A%20%3Chttps%3A%2F%2Fsweopendata.wikibase.cloud%2Fentity%2F%3E%0APREFIX%20wbt%3A%20%3Chttps%3A%2F%2Fsweopendata.wikibase.cloud%2Fprop%2Fdirect%2F%3E%0A%0ASELECT%20distinct%20%3FrLabel%20%3Fvideo%20%3Fcoord%20%3Fimg%20%3FwdQ%20%3FsvWikipedia%20WHERE%20%7B%0A%20%20VALUES%20%20%3FAnslagsTavla%20%7Bwb%3AQ240%7D%0A%20%20%20%3Fr%20wbt%3AP2%20%3FAnslagsTavla%20.%0A%20%20%20%3Fr%20wbt%3AP11%20%3Fvideo.%0A%20%20%3Fr%20wbt%3AP1%20%3FwdQ%0A%20%20BIND%28URI%28concat%28%22http%3A%2F%2Fwww.wikidata.org%2Fentity%2F%22%2C%3FwdQ%29%29%20AS%20%3Fwikidata_iri%29%0A%20%20%0A%20SERVICE%20%3Chttps%3A%2F%2Fquery.wikidata.org%2Fsparql%3E%20%7B%0A%20%20%20%20%3Fwikidata_iri%20wdt%3AP625%20%3Fcoord.%0A%20%20%20OPTIONAL%20%7B%20%3Fwikidata_iri%20wdt%3AP41%20%3Fflag%20%7D%0A%20%20%20OPTIONAL%20%7B%20%3Fwikidata_iri%20wdt%3AP94%20%3Fcoat%20%7D%0A%20%20%20OPTIONAL%20%7B%20%3Fwikidata_iri%20wdt%3AP154%20%3Flogo%20%7D%0A%20%20%20OPTIONAL%20%7B%20%3Fwikidata_iri%20wdt%3AP18%20%3Fimage%20%7D%20%20%0A%20%20%20BIND%28%20COALESCE%28%3Fflag%2C%20%3Fcoat%2C%20%3Flogo%2C%20%3Fimage%29%20as%20%3Fimg%20%29%0A%20%20%20OPTIONAL%20%7B%0A%20%20%20%20%20%20%3FsvWikipedia%20schema%3Aabout%20%3Fwikidata_iri%20.%0A%20%20%20%20%20%20%3FsvWikipedia%20schema%3AinLanguage%20%22sv%22%20.%0A%20%20%20%20%20%20%3FsvWikipedia%20schema%3AisPartOf%20%3Chttps%3A%2F%2Fsv.wikipedia.org%2F%3E%20.%0A%20%20%20%20%7D%0A%20%20%20%20%7D%0A%09SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22sv%2Cen%22.%20%7D%0A%7D) bör alla blandas in så denna yta skapades av mig Magnus Sälgö med hopp om att fler hoppar på...
* Synpunkter/tankar lämnas i <a href="https://github.com/salgo60/Anslagstavla/issues">Issues</a>

## POC Anslagstavla / Wikidata / Wikipedia
Efter att ha sett hur spretigt [290 kommuner skapar 290 SILOS](https://sweopendata.wikibase.cloud/query/embed.html#%23%23title%3A%20Kommuners%20Anslagstavla%20-%20test%20Wikibase%0A%23defaultView%3AMap%7B%22hide%22%3A%5B%22%3Fcoord%22%5D%7D%0A%0APREFIX%20wb%3A%20%3Chttps%3A%2F%2Fsweopendata.wikibase.cloud%2Fentity%2F%3E%0APREFIX%20wbt%3A%20%3Chttps%3A%2F%2Fsweopendata.wikibase.cloud%2Fprop%2Fdirect%2F%3E%0A%0ASELECT%20distinct%20%3FrLabel%20%3Fvideo%20%3Fcoord%20%3Fimg%20%3FwdQ%20%3FsvWikipedia%20WHERE%20%7B%0A%20%20VALUES%20%20%3FAnslagsTavla%20%7Bwb%3AQ240%7D%0A%20%20%20%3Fr%20wbt%3AP2%20%3FAnslagsTavla%20.%0A%20%20%20%3Fr%20wbt%3AP11%20%3Fvideo.%0A%20%20%3Fr%20wbt%3AP1%20%3FwdQ%0A%20%20BIND%28URI%28concat%28%22http%3A%2F%2Fwww.wikidata.org%2Fentity%2F%22%2C%3FwdQ%29%29%20AS%20%3Fwikidata_iri%29%0A%20%20%0A%20SERVICE%20%3Chttps%3A%2F%2Fquery.wikidata.org%2Fsparql%3E%20%7B%0A%20%20%20%20%3Fwikidata_iri%20wdt%3AP625%20%3Fcoord.%0A%20%20%20OPTIONAL%20%7B%20%3Fwikidata_iri%20wdt%3AP41%20%3Fflag%20%7D%0A%20%20%20OPTIONAL%20%7B%20%3Fwikidata_iri%20wdt%3AP94%20%3Fcoat%20%7D%0A%20%20%20OPTIONAL%20%7B%20%3Fwikidata_iri%20wdt%3AP154%20%3Flogo%20%7D%0A%20%20%20OPTIONAL%20%7B%20%3Fwikidata_iri%20wdt%3AP18%20%3Fimage%20%7D%20%20%0A%20%20%20BIND%28%20COALESCE%28%3Fflag%2C%20%3Fcoat%2C%20%3Flogo%2C%20%3Fimage%29%20as%20%3Fimg%20%29%0A%20%20%20OPTIONAL%20%7B%0A%20%20%20%20%20%20%3FsvWikipedia%20schema%3Aabout%20%3Fwikidata_iri%20.%0A%20%20%20%20%20%20%3FsvWikipedia%20schema%3AinLanguage%20%22sv%22%20.%0A%20%20%20%20%20%20%3FsvWikipedia%20schema%3AisPartOf%20%3Chttps%3A%2F%2Fsv.wikipedia.org%2F%3E%20.%0A%20%20%20%20%7D%0A%20%20%20%20%7D%0A%09SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22sv%2Cen%22.%20%7D%0A%7D) och ingen styr upp saker och ting, ingen vision finns att jobba ihop och skapa lösningar som sitter ihop och baseras på exempelvis [länkade data](https://sv.wikipedia.org/wiki/L%C3%A4nkade_data) så gjordes en [liten POC](https://github.com/salgo60/ProjectOutdoorGyms/issues/120#issuecomment-1242183361) se [video](https://www.youtube.com/watch?v=YNILvlAW3SM)


![image](https://user-images.githubusercontent.com/14206509/193144234-9ea62c6e-89f2-4be9-8dc9-c4061e6a57e0.png)

En variant är om vi kan koppla ihop Wikipedia med dokument i Anslagstavlor kanske mha <a target=_blank href="https://sweopendata.wikibase.cloud/wiki/Kommuner">Wikibase.cloud</a> dvs. en "kopia" av Wikidata
* Synpunkter/tankar lämnas i <a href="https://github.com/salgo60/Anslagstavla/issues">Issues</a>
* Test sidorför POC:en
  *  <a target="_blank" href="https://www.wikidata.org/wiki/Special:GoToLinkedPage/svwiki/Q10728573" target="_blank">Överförmyndare</a> / <a target="_blank" href="https://www.wikidata.org/wiki/Special:GoToLinkedPage/fiwiki/Q10728573">fi</a>
  *  <a target="_blank" href="https://www.wikidata.org/wiki/Special:GoToLinkedPage/svwiki/Q60970797">Kulturnämnd</a>

## Kommunallagen
Är relativt tydlig vad som gäller och pekar på att en websida kan användas!!! en av få gånger jag tycker våra lagstiftare pekar på digitala lösningars möjligheter.... **Felet** tror jag är att dom inte tar höjd och pekar på Öppna data.... konsekvenserna att inte tänka Digitalt först redan i kommunallagen är massa silos se tankar [community.dataportal.se/topic/486](https://community.dataportal.se/topic/486/guide-%C3%B6ver-hur-man-g%C3%B6r-en-serief%C3%B6rfr%C3%A5gan-till-myndigheter-p%C3%A5-handlingar-se) [IA](https://web.archive.org/web/20220930120307/https://community.dataportal.se/topic/486/guide-%C3%B6ver-hur-man-g%C3%B6r-en-serief%C3%B6rfr%C3%A5gan-till-myndigheter-p%C3%A5-handlingar-se)
<img width="715" alt="image" src="https://user-images.githubusercontent.com/14206509/193219069-2d5acc21-ec90-46aa-8384-f8a63c33ca98.png">

* [SFS 2017:725](https://www.riksdagen.se/sv/dokument-lagar/dokument/svensk-forfattningssamling/kommunallag-2017725_sfs-2017-725)

## Misc
* [POC](https://github.com/salgo60/ProjectOutdoorGyms/issues/120#issuecomment-1242183361)
  * [Wikibase.cloud sweopendata](https://sweopendata.wikibase.cloud/wiki/Kommuner)
* Bok om [Kunskapsgrafer](https://kgbook.org/) av Ying Ding et al... video med henne ["Scalable Graph Search & Graph Mining"](https://watch.knowledgegraph.tech/videos/ying-ding-katana-graph-solutions-scalable-graph-search-graph-mining)
[<img width="300" alt="image" src="https://user-images.githubusercontent.com/14206509/193150119-de0c62ef-3026-4581-ab05-583cfe33f200.png">](https://kgbook.org/)

# Osa 4 - Syväoppiminen harjoitustyö (15 p)

Syväoppiminen -koulutuksen opiskelijat voivat arvosanan, joka on yli 3, vain tekemällä
harjoitustyön.

Suosittelen myös sitä, että teette tämän tehtävän **parityönä** - etuina kun tehdään parityönä: 

* realistisempi aihevalinta mahdollista
* kommunikaatio välttämätöntä
* "vertaistuki" 
* pohdinta ja analyysi ovat asioita, joita kone/syväoppiminen vaativat, sitä on yksikseen hieman haastava tehdä

Toki työnjako ja kommunikaatio vievät aikaa, mutta näitä on hyvä harjoitella ennen reaalimaailman projekteja. Nykyaikana kehitystyötä harvemmin tehdään yksikseen vaan yleensä osana tiimiä.

Lähtökohta on, että harjoitustyö kannattaa tehdä, jos:
* Pidät haastavista tehtävistä
* Hyvä motivaatio tekoäly-opintoihin
* Hyvä perusosaaminen ja hyvät arvosanat kaikista muista AI&DA -opintojaksoista
* Riittävästi aikaa harjoitustyön tekemiseen ja tulosten dokumentointiin sekä niiden analysointiin

Muuten työn tekeminen ei ole välttämätöntä, vaan voi keskittyä oppimiseen muilla tavoin. Esim. 

* videokurssit syväoppimisesta 
* tai pienet lisätehtävät omatoimisesti
* ks. esim. DataCamp-alustan kurssit.

ovat erinomainen vaihtoehto syväoppimisen ymmärtämisen ja lisäopin saamisen kannalta.


## Tehtävä 4-0
### Aiheen valinta

Valitse aihe itsenäisesti ja sovi siitä ennen tekemistä opettajan kanssa lähettämällä aihe ja
sen kuvaus opettajalle esim. sähköpostiviestinä. Aihe pitää siis hyväksyttää ennen aloittamista.

Kuvaa ainakin seuraavat asiat:

* Ketä ryhmään kuuluu
* Aiheen kuvaus lyhyesti
* Työssä käytettävä datalähde tai -lähteet
* Millä teknologioilla toteutus tehdään

Aihekuvaukseen käytetään maksimissaan yksi A4-sivu. Aiheen hyväksymisen jälkeen voit aloittaa tehtävän tekemisen.

## Tehtävä 4-1
### Aihe: Syväoppimisen toteutussuunnitelma + aineiston valinta (3 p)

1. Valitse aineistosi tehtävään vapaasti esimerkiksi oman kiinnostuksen tai työn pohjalta. 
   * Tutustu aineistoon kunnolla
2. Esikäsittele data 
   * optimoi koneoppimismallille syötettävää dataa
   * voit poistaa "tarpeettomat piirteet" oman harkinnan mukaan
   * tee poikkeavien tai tyhjien data-arvojen käsittely
3. Normalisoi data 
   * Valitse sopiva skaalaustapa
4. Valitse luokkamuuttuja 
5. Visualisoi dataa muutamilla eri kuvioilla. 

## Tehtävä 4-2
### Aihe: Syväoppimisen toteutus (8 p)

1. Valitse sovellettava(t) syväoppimismalli(t) tehtävää varten
   *  Voit kokeilla esim. kahta eri tapaa
   *  Hyperparametrien kokeileminen parempien tuloksien saamiseksi on myös suotavaa
   *  Vertailun vuoksi toteutus kannattaa tehdä myös jollakin soveltuvalla koneoppimismallilla
2. Jaa aineisto koulutus- ja testausaineistoon
3. Toteuta syväoppiminen valitulla algoritmilla
   *  Se voi olla myös kurssin luentojen ulkopuolelta haettu menetelmä tai algoritmi
   * Kirjastokin voi olla joku muu kuten `PyTorch`
4. Laske luokittelutuloksen ennusteen tarkkuus ja sekaannusmatriisi 
   *  laske myös mahdollisia muita tunnuslukuja
   *  tai laske vastaavasti regressiotuloksen tarkkuus, jos kyseessä regressio-ongelma

Huom! kannattaa pitää muistiota kehitystyön aikana, johon keräät eri ajojen tulokset (tarkkuudet, ajoajat, mallikonfiguraatiot jne.).

## Tehtävä 4-3
### Aihe: Tulosten analysointi (4 p)

1. Analysoi ja vertaile malleilla saamiasi oppimistuloksia
2. Kuinka syväoppiminen eri menetelmillä sujui valitun aineiston ja valittujen menetelmien kohdalla
3. Kuinka hyvin menetelmä tai menetelmät toimi?
4. Mitä kehitettävää syväoppimismallissa tai esikäsittelyvaiheessa havaitset? 
   *  dokumentoi mahdolliset kehityskohteet
5. Kuinka voisit optimoida syväoppimismallia?
6. Muita huomioita tehtävästä?


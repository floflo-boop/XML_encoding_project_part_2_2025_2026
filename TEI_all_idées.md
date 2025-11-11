# Liste d'éléments/attributs qui peuvent m'être utile 

- [Liste d'éléments/attributs qui peuvent m'être utile](#liste-délémentsattributs-qui-peuvent-mêtre-utile)
  - [TEI HEADER](#tei-header)
    - [Rajouts](#rajouts)
    - [Ajouts](#ajouts)
  - [BODY](#body)

<br>
<br>

## TEI HEADER 

> à part les éléments déja présent à savoir : 

```XML
<fileDesc>
    <titleStmt>
        <title> </title>
    </titleStmt>
    <publicationStmt>
        <p>
    </publicationStmt>
    <sourceDesc>
        <p>
    </sourceDesc>

</fileDesc>
```
### Rajouts 

- `<sourceDesc>` description de la source  
  - `<msDesc>` description d'un manuscrit ou d'une source manuscrite 
    - `<History>` Histoire du manuscrit (possessions, acquisition)
    - `<msContents>` Le contenu intelectuel de la lettre (sans être un résumé)
    - `<msIdentifier>` Un numéro de côte pour le trouver 
      - `<country>`Germany`</country>`
      - `<settlement>`Leeipzig`</settlement>`
      - `<repository>`Universitätsbibliothek`</repository>`
  
<br>

  - `<PhysDesc>` Description physique 
     - `<objectDesc>` Description de l'objet 
       - `<supportDesc>`
      - `<handDesc>` Si il y a plusieurs main 

### Ajouts 


- `<profileDesc>` pour préciser les langages utilisés, le contexte de production, les personnes concernées par le contenu du texte. Il s'accompagne de : 
  - `<abstract>` afin d'offrir un résumé du document 
  - `<correspDesc>` permet de contenir ce qui concerne la correspondance (envoie, reçu)
    - Va contenir `<correspAction>` pour les envois, la réception, tout ça; et `<correspContext>` pour le remettre dans son contexte épistolaire donc si y une lettre avant ou après. 

```XML

<correspDesc> 
 <correspAction type="sent"> <!-- permet de définir une première action, ici l'envoie -->
  <persName>Carl Maria von Weber</persName> <!-- personne qui écrit et envoie la lettre -->
  <settlement>Dresden</settlement> <!-- d'où la lettre est envoyées -->
  <date when="1817-06-23">23 June 1817</date> <!-- quand la lettre est envoyées -->
 </correspAction>
 <correspAction type="received"> <!-- Seconde action, ici la réception-->
  <persName>Caroline Brandt</persName> <!-- la destinataire -->
  <settlement>Prag</settlement> <!-- l'endroit de destination-->
 </correspAction>
 <correspContext> <!-- contexte de la correspondance-->
  <ref type="prev"
   target="http://www.weber-gesamtausgabe.de/A041209">Previous letter of
  <persName>Carl Maria von Weber</persName> 
     to <persName>Caroline Brandt</persName>:
  <date from="1817-06-19" to="1817-06-20">June 19/20, 1817</date>
  </ref> <!-- permet de préciser une lettre précédentes, à laquelle il répond par exemple -->
  <ref type="next"
   target="http://www.weber-gesamtausgabe.de/A041217">Next letter of
  <persName>Carl Maria von Weber</persName> to
  <persName>Caroline Brandt</persName>:
  <date when="1817-06-27">June 27, 1817</date>
  </ref> <!-- permet de préciser si il y a eu une réponse à la lettre-->
 </correspContext>
</correspDesc>

```


  - `<creation>` contexte de production 
  - `<langUsage>` précise les langues utilisées y compris dialecte. 
    - peut contenir la balise `<language>` qui a un attribut @ident et @usage


- `<encodingDesc>` pour tout ce qui est relatif à l'encodage réalisé
  - `<editorialDecl>` pour tout ce qui est normalisation, etc 
  - `<projectDesc>` pour tout ce qui est relatif au projet poursuivis dans cette encodage (les motifs etc)
  - 


<br>
<br>

## BODY

- `<model.divTopPart>` groupe tous les éléments ne pouvant à paraître qu'au début d'un texte
  - `<Opener>` groupe tous les éléments constituant le début d'une lettre. La salutation, la date d'écriture, le lieu d'écriture, etc. 
    - `<byline>` contient la mention principale de responsabilité figurant sur la page de titre ou en tête ou en queue de l'ouvrage.  
    - `<dateline>` contient les informations sur le lieu d'écriture (`<name @place>`) et la date d'écriture (`<date>`)
    - `<salute>` contient la phrase de salutation, "à ma chère épouse" par exemple est une salutation.  
    - `<signed>` contient la signature d'une lettre. Peut s'accompagner d'un `@lang` si la manière de signer est spécifique à un langage. 

<br>

- `<mode.divBottomPart>` groupe tous les éléments ne pouvant à paraître qu'à la fin d'un texte
- `<Closer>` groupe tous les éléments constituant la fin d'une lettre. La signature, dates, lieu
  - `<byline>` contient la mention principale de responsabilité figurant sur la page de titre ou en tête ou en queue de l'ouvrage.
  - `<dateline>` contient les informations sur le lieu d'écriture (`<name @place>`) et la date d'écriture (`<date>`)
  - `<salute>` contient la phrase de salutation, "à ma chère épouse" par exemple est une salutation.  
  - `<signed>` contient la signature d'une lettre. Peut s'accompagner d'un `@lang` si la manière de signer est spécifique à un langage. 

- `<postscript>` pour encoder un élément survenant après un la lettre en elle même

- `<w>` pour encoder un mot. Peut s'accompagner d'un `@type` pour précise que c'est du langage de tranché par exemple.
  - Il peut contenir l'élément `<choice>`
    - Ce dernier peut contenir `<orig>` qui précise le mot de base, celui inscrit dans la lettre 
    - Et `<corr>` une version corrigé du mot précédent
    - Tous peuvent acceuillir les attribut `@ana` et `@type` pour préciser les raisons des choix
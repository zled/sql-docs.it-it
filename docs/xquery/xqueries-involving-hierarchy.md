---
title: Query XQuery relative alle gerarchia | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- hierarchies [XQuery]
- XQuery, hierarchies
ms.assetid: 6953d8b7-bad8-4b64-bf7b-12fa4f10f65c
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3296807e7470c84a4df2f3960ea01185c5915048
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47597060"
---
# <a name="xqueries-involving-hierarchy"></a>Esecuzione di query XQuery che coinvolgono gerarchie
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La maggior parte degli **xml** colonne di tipo i **AdventureWorks** database sono documenti semistrutturati. I documenti archiviati nelle diverse righe possono pertanto avere aspetti diversi. Le query di esempio contenute in questo argomento illustrano come estrarre informazioni dai vari documenti.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-from-the-manufacturing-instructions-documents-retrieve-work-center-locations-together-with-the-first-manufacturing-step-at-those-locations"></a>A. Recupero delle posizioni dei centri di lavorazione, insieme al primo passaggio di produzione eseguito in tali centri, dai documenti contenenti le istruzioni per la produzione  
 Per il modello di prodotto 7, la query costruisce codice XML che include il <`ManuInstr`> elemento, con **ProductModelID** e **ProductModelName** attributi e uno o più <`Location`> elementi figlio.  
  
 Ogni elemento <`Location`> ha un proprio set di attributi e un elemento figlio <`step`>. L'elemento figlio <`step`>; corrisponde al primo passaggio di produzione eseguito nel centro di lavorazione.  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
   \<ManuInstr  ProdModelID = "{sql:column("Production.ProductModel.ProductModelID") }"   
                ProductModelName = "{ sql:column("Production.ProductModel.Name") }" >  
            {   
              for $wc in //AWMI:root/AWMI:Location  
              return  
                <Location>  
                 {$wc/@* }  
                 <step1> { string( ($wc//AWMI:step)[1] ) } </step1>  
                </Location>  
            }  
          </ManuInstr>  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   Il **dello spazio dei nomi** parola chiave nel [prologo XQuery](../xquery/modules-and-prologs-xquery-prolog.md) definisce un prefisso dello spazio dei nomi. Tale prefisso verrà utilizzato in seguito nel corpo della query.  
  
-   I token per lo scambio di contesto, {) e (}, vengono utilizzati nella query per passare dalla costruzione delle informazioni XML alla valutazione della query.  
  
-   Il **Column** viene usato per includere un valore relazionale nel codice XML che viene costruito.  
  
-   Nella creazione dell'elemento <`Location`> $wc/@* recupera tutti gli attributi dei centri di lavorazione.  
  
-   Il **String ()** funzione restituisce il valore di stringa dal <`step`> elemento.  
  
 Risultato parziale:  
  
```  
<ManuInstr ProdModelID="7" ProductModelName="HL Touring Frame">  
   <Location LocationID="10" SetupHours="0.5"   
            MachineHours="3" LaborHours="2.5" LotSize="100">  
     <step1>Insert aluminum sheet MS-2341 into the T-85A   
             framing tool.</step1>  
   </Location>  
   <Location LocationID="20" SetupHours="0.15"   
            MachineHours="2" LaborHours="1.75" LotSize="1">  
      <step1>Assemble all frame components following   
             blueprint 1299.</step1>  
   </Location>  
...  
</ManuInstr>   
```  
  
### <a name="b-find-all-telephone-numbers-in-the-additionalcontactinfo-column"></a>B. Ricerca di tutti i numeri di telefono nella colonna AdditionalContactInfo  
 La query seguente recupera i numeri di telefono aggiuntivi per un determinato contatto presso un cliente cercando l'elemento <`telephoneNumber`> nell'intera gerarchia. Poiché l'elemento <`telephoneNumber`> può presentarsi ovunque nella gerarchia, la query utilizza l'operatore descendant and self (//).  
  
```  
SELECT AdditionalContactInfo.query('  
 declare namespace ci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
 declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
for $ph in /ci:AdditionalContactInfo//act:telephoneNumber  
   return  
      $ph/act:number  
') as x  
FROM  Person.Contact  
WHERE ContactID = 1  
```  
  
 Risultato:  
  
```  
\<act:number   
  xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
  111-111-1111  
\</act:number>  
\<act:number   
  xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
  112-111-1111  
\</act:number>  
```  
  
 Per recuperare solo i numeri di telefono di livello principale, in particolare gli elementi figlio <`telephoneNumber`> di <`AdditionalContactInfo`>, l'espressione FOR utilizzata nella query viene modificata come segue:  
  
 `for $ph in /ci:AdditionalContactInfo/act:telephoneNumber` (Indici per tabelle con ottimizzazione per la memoria).  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali su XQuery](../xquery/xquery-basics.md)   
 [Costruzione di strutture XML &#40;XQuery&#41;](../xquery/xml-construction-xquery.md)   
 [Dati XML &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)  
  
  

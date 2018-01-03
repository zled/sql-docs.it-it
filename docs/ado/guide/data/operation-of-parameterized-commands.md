---
title: Funzionamento dei comandi con parametri | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data shaping [ADO], parameterized commands
- parameterized commands [ADO]
ms.assetid: 4fae0d54-83b6-4ead-99cc-bcf532daa121
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 658d0dc9baa22006b327d826effb5687ccbc1822
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="operation-of-parameterized-commands"></a>Funzionamento dei comandi con parametri
Se si lavora con un elemento figlio di grandi dimensioni **Recordset**, in particolare rispetto alla dimensione dell'elemento padre **Recordset**, ma è necessario accedere solo ad alcuni capitoli figlio, potrebbe essere preferibile utilizzare un comando con parametri.  
  
 Oggetto *comando senza parametri* recupera intero padre e figlio **recordset**, aggiunge una colonna a capitoli all'elemento padre e quindi assegna un riferimento al capitolo figlio correlati per ogni riga padre .  
  
 Oggetto *comando con parametri* recupera l'oggetto padre intero **Recordset**, ma recupera solo il capitolo **Recordset** accesso alla colonna del capitolo. Questa differenza di una strategia di recupero può produrre vantaggi significativi delle prestazioni.  
  
 Ad esempio, è possibile specificare quanto segue:  
  
```  
SHAPE {SELECT * FROM customer}   
   APPEND ({SELECT * FROM orders WHERE cust_id = ?}   
   RELATE cust_id TO PARAMETER 0)  
```  
  
 Le tabelle padre e figlio dispongono un nome di colonna, cust_id*.* Il *comando figlio* ha un "?" segnaposto, a cui fa riferimento la clausola RELATE (ovvero, "... PARAMETRO 0").  
  
> [!NOTE]
>  La clausola di parametro relativo esclusivamente per la sintassi del comando forma. Non è associata a uno ADO [parametro](../../../ado/reference/ado-api/parameter-object.md) oggetto o [parametri](../../../ado/reference/ado-api/parameters-collection-ado.md) insieme.  
  
 Quando viene eseguito il comando con parametri di forma, si verifica quanto segue:  
  
1.  Il *comando padre* viene eseguita e restituisce un elemento padre **Recordset** dalla tabella Customers.  
  
2.  Una colonna a capitoli viene aggiunto all'elemento padre **Recordset**.  
  
3.  Quando si accede alla colonna del capitolo di una riga padre, il *comando figlio* viene eseguita utilizzando il valore di Customer. cust_id come valore del parametro.  
  
4.  Tutte le righe nel set di righe del provider dati creato nel passaggio 3 vengono utilizzate per popolare l'elemento figlio **Recordset**. In questo esempio, ovvero tutte le righe della tabella ordini in cui il cust_id è uguale al valore di Customer. cust_id. Per impostazione predefinita, l'elemento figlio **Recordset**s verranno memorizzate nel client fino a quando tutti i riferimenti all'elemento padre **Recordset** vengono rilasciati. Per modificare questo comportamento, impostare il **Recordset** [proprietà dinamica](../../../ado/reference/ado-api/ado-dynamic-property-index.md) **righe figlio Cache** a **False**.  
  
5.  Un riferimento alle righe figlio recuperati (vale a dire il capitolo dell'elemento figlio **Recordset**) viene inserito nella colonna del capitolo della riga corrente dell'elemento padre **Recordset**.  
  
6.  Quando si accede alla colonna del capitolo di un'altra riga, vengono ripetuti i passaggi 3-5.  
  
 Il **righe figlio Cache** proprietà dinamica è impostata su **True** per impostazione predefinita. Il comportamento di memorizzazione nella cache varia in base ai valori di parametro della query. In una query con un solo parametro, l'elemento figlio **Recordset** per un determinato parametro valore verrà memorizzato tra le richieste di un elemento figlio con tale valore. Il codice seguente illustra questo processo:  
  
```  
SCmd = "SHAPE {select * from customer} " & _  
         "APPEND({select * from orders where cust_id = ?} " & _  
         "RELATE cust_id TO PARAMETER 0) AS chpCustOrder"  
Rst1.Open sCmd, Cnn1  
Set RstChild = Rst1("chpCustOrder").Value  
Rst1.MoveNext      ' Next cust_id passed to Param 0, & new rs fetched   
                   ' into RstChild.  
Rst1.MovePrevious  ' RstChild now holds cached rs, saving round trip.  
```  
  
 In una query con due o più parametri, un figlio memorizzati nella cache viene utilizzato solo se tutti i valori dei parametri corrispondono ai valori memorizzati nella cache.  
  
## <a name="parameterized-commands-and-complex-parent-child-relations"></a>I comandi con parametri e relazioni complesse padre-figlio  
 Oltre a utilizzare i comandi con parametri per migliorare le prestazioni di una gerarchia di tipo equijoin, è possono utilizzare i comandi con parametri per supportare le relazioni padre-figlio più complesse. Si consideri ad esempio un database lega con due tabelle: un sistema costituito il team (team_id, nome_team) e l'altro dei giochi (data, home_team, visiting_team).  
  
 Uso di una gerarchia senza parametri, non è possibile correlare le tabelle di giochi e i team in modo che l'elemento figlio **Recordset** per ogni team contiene la pianificazione completa. È possibile creare capitoli che contengono la pianificazione iniziale o la pianificazione di viaggio, ma non entrambi. Infatti, la clausola RELATE è limitato a relazioni padre-figlio del form (pc1 = cc1) AND (pc2 = pc2). In tal caso, se il comando include "RELATE team_id TO home_team, team_id TO visiting_team", si otterrebbe solo giochi in cui un team è stata la riproduzione di se stesso. Si desidera è "(team_id=home_team) o (team_id = visiting_team)", ma il provider Shape non supporta la clausola OR.  
  
 Per ottenere il risultato desiderato, è possibile utilizzare un comando con parametri. Ad esempio  
  
```  
SHAPE {SELECT * FROM teams}   
APPEND ({SELECT * FROM games WHERE home_team = ? OR visiting_team = ?}   
        RELATE team_id TO PARAMETER 0,   
               team_id TO PARAMETER 1)   
```  
  
 In questo esempio sfrutta la maggiore flessibilità della clausola WHERE SQL per ottenere il risultato che è necessario.  
  
> [!NOTE]
>  Quando tramite le clausole WHERE, i parametri non consente i tipi di dati SQL per text, ntext e image o verrà generato un errore che contiene la descrizione seguente: `Invalid operator for data type`.  
  
## <a name="see-also"></a>Vedere anche  
 [Data Shaping di esempio](../../../ado/guide/data/data-shaping-example.md)   
 [Grammatica formale forma](../../../ado/guide/data/formal-shape-grammar.md)   
 [Comandi Shape in generale](../../../ado/guide/data/shape-commands-in-general.md)

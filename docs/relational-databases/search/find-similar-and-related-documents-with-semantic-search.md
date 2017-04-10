---
title: "Trovare documenti simili e correlati tramite la ricerca semantica | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ricerca semantica [SQL Server], query di somiglianza dei documenti"
ms.assetid: 9f527883-031b-442f-8e95-24bc0151ecbf
caps.latest.revision: 18
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 17
---
# Trovare documenti simili e correlati tramite la ricerca semantica
  Viene descritto come reperire documenti o valori di testo simili o correlati, nonché informazioni relative alla somiglianza o correlazione, in colonne configurate per l'indicizzazione semantica statistica.  
  
##  <a name="BasicsQuerySimilar"></a> Trovare documenti simili o correlati  
  
###  <a name="HowToQuerySimilar"></a> Procedura: trovare documenti simili o correlati con SEMANTICSIMILARITYTABLE  
 Per identificare documenti simili o correlati in una colonna specifica, eseguire una query sulla funzione [semanticsimilaritytable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritytable-transact-sql.md).  
  
 **SEMANTICSIMILARITYTABLE** restituisce una tabella di zero, una o più righe per le colonne il cui contenuto nella colonna specificata è semanticamente simile a un documento specificato. A questa funzione del set di righe è possibile fare riferimento nella clausola FROM di un'istruzione SELECT come normale nome di tabella.  
  
 Non è possibile eseguire una query su diverse colonne per ottenere documenti simili. La funzione **SEMANTICSIMILARITYTABLE** recupera risultati solo dalla stessa colonna specificata come colonna di origine, identificata dall'argomento **source_key**.  
  
 Per informazioni dettagliate sui parametri necessari per la funzione **SEMANTICSIMILARITYTABLE** e sulla tabella dei risultati restituita, vedere [semanticsimilaritytable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritytable-transact-sql.md).  
  
> [!IMPORTANT]  
>  Per le colonne di destinazione deve essere abilitata l'indicizzazione full-text e semantica.  
  
###  <a name="HowToIdentifySimilar"></a> Esempio: trovare i documenti più simili a un altro documento  
 Nell'esempio seguente vengono recuperati i primi 10 candidati simili al candidato specificato mediante *@CandidateID* dalla tabella HumanResources.JobCandidate nel database di esempio AdventureWorks2012.  
  
```scr  
SELECT TOP(10) KEY_TBL.matched_document_key AS Candidate_ID  
FROM SEMANTICSIMILARITYTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume,  
    @CandidateID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
GO  
```  
  
##  <a name="BasicsQuerySimilarity"></a> Trovare informazioni relative alla somiglianza o correlazione dei documenti  
  
###  <a name="HowToQuerySimilarity"></a> Procedura: trovare informazioni sulla somiglianza o correlazione dei documenti mediante SEMANTICSIMILARITYDETAILSTABLE  
 Per ottenere informazioni sulle frasi chiave che rendono simili o correlati alcuni documenti, è possibile eseguire una query sulla funzione [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql.md).  
  
 **SEMANTICSIMILARITYDETAILSTABLE** restituisce una tabella di zero, una o più righe di frasi chiave comuni in due documenti, ovvero un documento di origine e un documento corrispondente, il cui contenuto è semanticamente simile. A questa funzione del set di righe è possibile fare riferimento nella clausola FROM di un'istruzione SELECT come normale nome di tabella.  
  
 Per informazioni dettagliate sui parametri necessari per la funzione **SEMANTICSIMILARITYDETAILSTABLE** e sulla tabella dei risultati restituita, vedere [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql.md).  
  
> [!IMPORTANT]  
>  Per le colonne di destinazione deve essere abilitata l'indicizzazione full-text e semantica.  
  
###  <a name="HowToSimilarPhrases"></a> Esempio: trovare le frasi chiave più simili tra documenti  
 Nell'esempio seguente vengono recuperate le 5 frasi chiave associate al punteggio di somiglianza più elevato tra i candidati specificati nella tabella **HumanResources.JobCandidate** del database di esempio AdventureWorks2012.  
  
```tsql  
SELECT TOP(5) KEY_TBL.keyphrase, KEY_TBL.score  
FROM SEMANTICSIMILARITYDETAILSTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume, @CandidateID,  
    Resume, @MatchedID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
GO  
```  
  
  
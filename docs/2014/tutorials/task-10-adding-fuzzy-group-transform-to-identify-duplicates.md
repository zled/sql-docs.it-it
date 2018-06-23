---
title: 'Attività 10: Aggiunta della trasformazione Raggruppamento Fuzzy per identificare i duplicati | Documenti Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 90b2b323-babd-464a-8914-9dc5e66aca74
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: cf9ad3dff4737d7308e7ec3434985b18015f29d8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068176"
---
# <a name="task-10-adding-fuzzy-group-transform-to-identify-duplicates"></a>Attività 10: Aggiunta della trasformazione Raggruppamento fuzzy per l'identificazione di duplicati
  In questa attività viene aggiunta una trasformazione Raggruppamento fuzzy al flusso di dati. La trasformazione Raggruppamento fuzzy consente di identificare i duplicati nei dati di origine. Vedere [la trasformazione Raggruppamento Fuzzy](http://msdn.microsoft.com/library/ms141764.aspx) per altri dettagli.  
  
1.  Trascinare **raggruppamento Fuzzy** trasforma nello **altre trasformazioni** sul **casella degli strumenti SSIS** per il **del flusso di dati** disponibile nella scheda  **Combina record corretti e con correzione**.  
  
2.  Fare doppio clic su **raggruppamento Fuzzy** trasformare il **del flusso di dati** scheda e fare clic su **rinominare**. Tipo di **Raggruppa fornitori con ID corrispondenti** e premere **invio**.  
  
3.  Connettersi **combina record corretti e** alla **Raggruppa fornitori con ID corrispondenti** utilizzando il collegamento blu.  
  
     ![Connessione a Raggruppa fornitori con ID corrispondenti](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-01.jpg "connessione a Raggruppa fornitori con ID corrispondenti")  
  
4.  Fare doppio clic su **Raggruppa fornitori con ID corrispondenti**.  
  
5.  Nel **Editor trasformazione Raggruppamento Fuzzy**, fare clic su **New** accanto a **gestione connessione OLE DB nell'elenco** per avviare **configurare connessione OLE DB Gestione** finestra di dialogo.  
  
6.  Nella finestra di dialogo, fare clic su **New** per avviare **Connection Manager** finestra di dialogo.  
  
7.  Tipo di **(locale)** oppure **periodo** (.) per il nome del Server.  
  
8.  Selezionare **MDS** per **selezionare o immettere un nome di database** campo. Si utilizzerà il database MDS come archiviazione temporanea per il **trasformazione Raggruppamento Fuzzy**. Il **raggruppamento Fuzzy** la trasformazione richiede una connessione a un'istanza di SQL Server per creare le tabelle temporanee di SQL Server che richiede l'algoritmo di trasformazione di eseguire il lavoro. A tal fine, è possibile creare un database o utilizzarne un altro esistente.  
  
9. Fare clic su **Test connessione** per testare la connessione e fare clic su **OK** nella finestra di messaggio.  
  
10. Nel **gestione connessione** finestra di dialogo, fare clic su **OK**.  
  
11. Selezionare **(local). MDS** (o **localhost. MDS**) dal **elenco di connessioni dati** e fare clic su **OK**.  
  
12. Nel **Editor trasformazione Raggruppamento Fuzzy**, verificare che **(local). MDS** o **localhost. MDS** sia selezionata per il **gestione connessione OLE DB**.  
  
13. Passare il **colonne** scheda.  
  
14. Select (casella di controllo) **SupplierID_Output** dall'elenco dei **colonne di Input disponibili**. Per configurare la trasformazione, selezionare le colonne di input da utilizzare per l'identificazione dei duplicati. Per mantenerla semplice, utilizzare solo SupplierID in questo passaggio.  
  
     ![Editor trasformazione Raggruppamento fuzzy](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-02.jpg "Editor trasformazione Raggruppamento Fuzzy")  
  
15. Fare clic su **OK** per chiudere la **Editor trasformazione Raggruppamento Fuzzy**.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 11: Aggiunta della trasformazione Suddivisione condizionale a Filtra duplicati](../../2014/tutorials/task-11-adding-conditional-split-transform-to-filter-duplicates.md)  
  
  
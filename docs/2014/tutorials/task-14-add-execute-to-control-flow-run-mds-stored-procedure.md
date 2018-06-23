---
title: 'Attività 14: Aggiunta di attività Esegui SQL al flusso di controllo per eseguire la Stored Procedure per MDS | Documenti Microsoft'
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
ms.assetid: 9a5d1b52-d505-4e6f-8a89-569329c094e2
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 3d364f3e0a2fbff167336bffa6ea5092d0954d14
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064164"
---
# <a name="task-14-adding-execute-sql-task-to-control-flow-to-run-the-stored-procedure-for-mds"></a>Attività 14: Aggiunta dell'Attività Esegui SQL al flusso di controllo per eseguire la stored procedure per MDS
  Dopo il caricamento dei dati nelle tabelle di staging MDS, eseguire una stored procedure associata alla tabella in questione per caricare i dati di staging nelle tabelle appropriate del database MDS. In questa stored procedure sono inclusi due parametri obbligatori che è necessario passare: LogFlag e VersionName. Il parametro LogFlag specifica se le transazioni vengono registrate durante il processo di gestione temporanea, mentre il parametro VersionName rappresenta la versione del modello. Vedere [staging Stored Procedure](http://msdn.microsoft.com/library/hh231028.aspx) per altre informazioni.  
  
 In questa attività viene aggiunta Attività Esegui SQL al flusso di controllo per richiamare la stored procedure in modo da caricare i dati di gestione temporanea nelle tabelle MDS appropriate.  
  
1.  A questo punto, passare per il **flusso di controllo** scheda.  
  
2.  Trascinare **attività Esegui SQL** dal **casella degli strumenti SSIS** per il **flusso di controllo** scheda.  
  
3.  Fare doppio clic su **attività Esegui SQL** nel **flusso di controllo** scheda e fare clic su **rinominare**. Tipo di **avvia Stored Procedure per caricare i dati in MDS** e premere **invio**.  
  
4.  Connettersi **Ricevi, Pulisci, corrispondenza e dati fornitore abbina** alla **avvia Stored Procedure per caricare i dati** utilizzando il connettore verde.  
  
     ![Connettersi all'attività Esegui SQL](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-01.jpg "connettersi all'attività Esegui SQL")  
  
5.  Utilizzando il **variabili** finestra, aggiungere due nuove variabili con le seguenti impostazioni. Se non viene visualizzato il **variabili** finestra, fare clic su **SSIS** nella barra dei menu e fare clic su **variabili**.  
  
    |nome|Tipo di dati|valore|  
    |----------|---------------|-----------|  
    |LogFlag|Int32|1|  
    |VersionName|String|VERSION_1|  
  
     ![Finestra variabili SSIS](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-02.jpg "finestra variabili SSIS")  
  
6.  Fare doppio clic su **attivano Stored Procedure per caricare i dati in MDS**.  
  
7.  Nel **Editor attività Esegui SQL** finestra di dialogo **(local). MDS** (o **localhost. MDS**) per **connessione**.  
  
8.  Tipo **EXEC [stg]. [ udp_Supplier_Leaf]?,?,?** per **istruzione SQL**. Per verificare il nome, utilizzare SQL Server Management Studio.  
  
     ![Eseguire finestra di dialogo Editor SQL - impostazioni generali](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-03.jpg "eseguire finestra di dialogo Editor SQL - impostazioni generali")  
  
9. Fare clic su **Mapping parametri** nel menu a sinistra.  
  
10. Nel **Mapping dei parametri** fare clic su **Add** per aggiungere un mapping. Ingrandire la finestra e ridimensionare le colonne in modo da visualizzare correttamente i valori negli elenchi a discesa.  
  
11. Selezionare **User:: VersionName** dall'elenco a discesa per il **il nome di variabile**.  
  
12. Selezionare **NVARCHAR** per **tipo di dati**.  
  
13. Tipo di **0** (zero) per **nome del parametro**.  
  
14. Ripetere i quattro passaggi precedenti per aggiungere altre due variabili.  
  
    |Nome variabile|Tipo di dati (importante)|Nome parametro|  
    |-------------------|-----------------------------|--------------------|  
    |User::LogFlag|LONG|1|  
    |User::BatchTag|NVARCHAR|2|  
  
     ![Editor attività Esegui SQL - Mapping dei parametri](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-04.jpg "Editor attività Esegui SQL - Mapping parametri")  
  
15. Fare clic su **OK** per chiudere la **Editor Esegui SQL** finestra di dialogo.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 15: Compilazione ed esecuzione del progetto SSIS](../../2014/tutorials/task-15-building-and-running-the-ssis-project.md)  
  
  
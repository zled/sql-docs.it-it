---
title: 'Attività 12: Aggiunta di trasformazione colonna derivata ad Aggiungi colonne richieste da MDS | Documenti Microsoft'
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
ms.assetid: 98ccb271-04da-4126-9729-67e9a479aaef
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b81dd18f0ba79167a66b5cdd09c2059fcd0e0a96
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36167978"
---
# <a name="task-12-adding-derived-column-transform-to-add-columns-required-by-mds"></a>Attività 12: Aggiunta della trasformazione Colonna derivata ad Aggiungi colonne richieste da MDS
  In questa attività viene aggiunta la trasformazione Colonna derivata al flusso di dati. Aggiungere due colonne derivate, **ImportType** e **BatchTag**, per i record passati a questa trasformazione. È consigliabile aggiungere queste colonne prima di caricare i dati nelle tabelle di staging in MDS. Queste due colonne sono necessarie per le tabelle di staging in MDS. Vedere [tabelle di gestione temporanea di membri foglia](http://msdn.microsoft.com/library/ee633854.aspx) per altri dettagli.  
  
1.  Trascinare **trasformazione colonna derivata** da **comuni** sezione il **casella degli strumenti SSIS** per il **del flusso di dati** scheda.  
  
2.  Fare doppio clic su **colonna derivata** trasformare il **del flusso di dati** scheda e fare clic su **rinominare**. Tipo di **Aggiungi colonne richieste da MDS** e premere **invio**.  
  
3.  Connettersi **Filtra duplicati** alla **Aggiungi colonne richieste da MDS** utilizzando il collegamento blu. Dovrebbe vedere il **selezione Input e Output** finestra di dialogo.  
  
4.  Nel **selezione Input e Output** finestra di dialogo **record univoci**, fare clic su **OK**.  
  
     ![Finestra di dialogo di selezione di Output di input](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-01.jpg "Output finestra di dialogo di selezione di Input")  
  
5.  Fare clic su **SSIS** nella barra dei menu e fare clic su **variabili**.  
  
6.  Nel **variabili** finestra, fare clic su **Aggiungi variabile** pulsante sulla barra degli strumenti.  
  
     ![Finestra variabili SSIS](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-02.jpg "finestra variabili SSIS")  
  
7.  Tipo di **ImportType** per il **nome** e **2** per il **valore**. Specificare il valore 2 dal momento che si desidera aggiungere nuovi membri a un'entità in MDS. Per informazioni dettagliate su questo parametro, vedere [tabella di gestione temporanea di membri foglia](http://msdn.microsoft.com/library/ee633854.aspx).  
  
8.  Fare clic su **Aggiungi variabile** nuovo clic sul pulsante della barra degli strumenti.  
  
9. Tipo di **BatchTag** per il **nome**, selezionare **stringa** per il **tipo di dati**, e **EIMBatch** per il **Valore**. **BatchTag** è solo un nome univoco per il batch che verrà inviato a MDS.  
  
10. Nel **flusso di dati** scheda, fare doppio clic su **Aggiungi colonne richieste da MDS**.  
  
11. Nel **Editor trasformazione colonna derivata** della finestra di dialogo il **casella di riepilogo nel riquadro inferiore**, tipo **ImportType** per il **nome colonna derivata**.  
  
12. Espandere **variabili e parametri** nel riquadro superiore sinistro trascinare **User:: importtype** per il **espressione** colonna.  
  
     ![Editor trasformazione colonna derivata](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-03.jpg "Editor trasformazione colonna derivata")  
  
13. Tipo di **BatchTag** nella riga successiva per il **nome colonna derivata**.  
  
14. Trascinare **User:: batchtag** da **variabili e parametri** per il **espressione** colonna.  
  
15. Fare clic su **OK** per chiudere la **trasformazione colonna derivata** finestra di dialogo.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 13: Aggiunta della destinazione OLE DB per scrivere dati nella tabella di gestione temporanea MDS](../../2014/tutorials/task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table.md)  
  
  
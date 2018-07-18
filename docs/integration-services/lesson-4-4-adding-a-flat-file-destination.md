---
title: 'Passaggio 4: Aggiunta di una destinazione file flat | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2016
ms.assetid: f4088de3-16d8-419c-96a1-a2cd005d0a5b
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a66649974ee1821388ad362aedb14cfd1d20f1c7
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35400213"
---
# <a name="lesson-4-4---adding-a-flat-file-destination"></a>Lezione 4-4 - Aggiunta di una destinazione file flat
L'output degli errori della trasformazione Lookup Currency Key reindirizza alla trasformazione Script tutte le righe di dati in cui l'operazione di ricerca ha avuto esito negativo. Per migliorare le informazioni sugli errori, la trasformazione Script esegue uno script che ottiene la descrizione degli errori.  
  
In questa attività, tutte queste informazioni sulle righe con esito negativo verranno salvate in un file delimitato per l'elaborazione in un momento successivo. Per salvare le righe con esito negativo, è necessario aggiungere e configurare una gestione connessione file flat per il file di testo che conterrà i dati degli errori e una destinazione file flat. Impostando le proprietà della gestione connessione file flat utilizzata dalla destinazione file flat è possibile specificare la modalità con cui la destinazione file flat deve formattare e scrivere il file di testo. Per altre informazioni, vedere [Gestione connessione file flat](../integration-services/connection-manager/flat-file-connection-manager.md) e [Destinazione file flat](../integration-services/data-flow/flat-file-destination.md).  
  
### <a name="to-add-and-configure-a-flat-file-destination"></a>Per aggiungere e configurare una destinazione file flat  
  
1.  Fare clic sulla scheda **Flusso di dati** .  
  
2.  Nella **Casella degli strumenti SSIS**espandere **Altro**e trascinare **Destinazione file flat** sull'area di progettazione del flusso di dati. Posizionare la **Destinazione file flat** direttamente sotto la trasformazione **Get Error Description** (Ottieni descrizione errore).  
  
3.  Fare clic sulla trasformazione **Get Error Description** (Ottieni descrizione errore) e quindi trascinare la freccia verde sulla nuova **Destinazione file flat**.  
  
4.  Nell'area di progettazione **Flusso di dati** fare clic su **Destinazione file flat** nella trasformazione **Destinazione file flat** appena aggiunta e impostare il nome su **Righe con errori**.  
  
5.  Fare clic con il pulsante destro del mouse sulla trasformazione **Righe con errori** , scegliere **Modifica**e quindi in **Editor destinazione file flat**fare clic su **Nuovo**.  
  
6.  Nella finestra di dialogo **Formato file flat** verificare che sia stato selezionato **Delimitato** e quindi scegliere **OK**.  
  
7.  In **Editor gestione connessione file flat**digitare **Error Data** nella casella **Nome gestione connessione**.  
  
8.  Nella finestra di dialogo **Editor gestione connessione file flat** fare clic su **Sfoglia**e individuare la cartella in cui archiviare il file.  
  
9. Nella finestra di dialogo **Apri** in **Nome file**digitare **ErrorOutput.txt**e quindi fare clic su **Apri**.  
  
10. Nella finestra di dialogo **Editor gestione connessione file flat** verificare che nella casella **Impostazioni locali** sia presente Inglese (Stati Uniti) e che nella **Tabella codici** sia presente 1252 (ANSI -Latino I).  
  
11. Nel riquadro delle opzioni fare clic su **Colonne**.  
  
    Si noti che oltre alle colonne del file dei dati di origine sono presenti tre nuove colonne: ErrorCode, ErrorColumn e ErrorDescription. Queste colonne vengono generate dall'output degli errori della trasformazione Lookup Currency Key e dallo script nella trasformazione Get Error Description e possono essere utilizzate per la risoluzione dei problemi relativi alla riga con esito negativo.  
  
12. Fare clic su **OK**.  
  
13. In **Editor destinazione file flat**deselezionare la casella di controllo **Sovrascrivi dati nel file** .  
  
    La deselezione di questa casella di controllo mantiene gli errori per più esecuzioni del pacchetto.  
  
14. In **Editor destinazione file flat**fare clic su **Mapping** per verificare che tutte le colonne siano corrette. Facoltativamente è possibile rinominare le colonne nella destinazione.  
  
15. Fare clic su **OK**.  
  
## <a name="next-steps"></a>Next Steps  
[Passaggio 5: Test del pacchetto creato nella lezione 4 dell'esercitazione](../integration-services/lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
  
  

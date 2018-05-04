---
title: Valutare gli schemi di DB2 per la conversione (DB2ToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-db2
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 8892f5a4-72ba-4406-8649-7a9d67f4c1d9
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 7fcba9fdd43756485c4dea43716539e56ee0c1e5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="assessing-db2-schemas-for-conversion-db2tosql"></a>Valutare gli schemi di DB2 per la conversione (DB2ToSQL)
Prima di caricare gli oggetti e la migrazione dei dati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è necessario determinare come complessa la migrazione sarà e quanto tempo richiederà la migrazione. SSMA è possibile creare un report di valutazione che mostra la percentuale di oggetti che verranno convertiti correttamente. SSMA consente inoltre di visualizzare i problemi specifici che provocano errori di conversione.  
  
## <a name="creating-assessment-reports"></a>Creazione di report di valutazione  
Quando viene creato il report di valutazione, SSMA converte gli oggetti di database DB2 selezionati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sintassi, quindi Mostra i risultati.  
  
**Per creare un report di valutazione**  
  
1.  Nel Visualizzatore metadati DB2, selezionare gli schemi da valutare.  
  
2.  Per omettere i singoli oggetti, deselezionare le caselle di controllo accanto a quelli.  
  
3.  Fare doppio clic su **schemi**, quindi selezionare **crea Report**.  
  
    È inoltre possibile analizzare singoli oggetti destro del mouse su un oggetto e quindi selezionando **crea Report**.  
  
    SSMA viene visualizzato lo stato nella barra di stato nella parte inferiore della finestra. Se il riquadro di Output è visibile, si verifica anche i messaggi nel riquadro di Output.  
  
    Al termine, la valutazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant per DB2: verrà visualizzata la finestra di Report di valutazione.  
  
## <a name="using-assessment-reports"></a>Utilizzo dei report di valutazione  
La finestra di Report di valutazione contiene tre riquadri:  
  
-   Il riquadro di sinistra contiene la gerarchia di oggetti inclusi nel report di valutazione. È possibile esplorare la gerarchia e selezionare gli oggetti e le categorie di oggetti da visualizzare codice e le statistiche di conversione.  
  
-   Il contenuto del riquadro di destra dipende dall'elemento selezionato nel riquadro a sinistra.  
  
    Se si seleziona un gruppo di oggetti, uno schema, o se viene selezionata una tabella, il riquadro di destra contiene un riquadro delle statistiche di conversione e oggetti dal riquadro delle categorie. Il riquadro delle statistiche di conversione sono indicate le statistiche di conversione per gli oggetti selezionati. Gli oggetti dal riquadro delle categorie sono indicate le statistiche di conversione per l'oggetto o le categorie di oggetti.  
  
    Se si seleziona una funzione, pacchetto, procedure, sequenza o visualizzazione, riquadro di destra contiene le statistiche, codice sorgente e codice di destinazione.  
  
    -   Nell'area superiore mostra le statistiche generali per l'oggetto. Potrebbe essere necessario espandere **statistiche** per visualizzare queste informazioni.  
  
    -   L'area di origine viene illustrato il codice di origine dell'oggetto selezionato nel riquadro a sinistra. Le aree evidenziate mostrano codice sorgente problematico.  
  
    -   L'area di destinazione Mostra il codice convertito. Testo di colore rosso Mostra messaggi di errore e di codice problematici.  
  
-   Nel riquadro inferiore mostra i messaggi di conversione, raggruppati in base al numero di messaggio. È possibile fare clic su **errori**, **avvisi**, o **Info** per visualizzare le categorie di messaggi e quindi espandere un gruppo di messaggi. Fare clic su un singolo messaggio per selezionare l'oggetto nel riquadro a sinistra e visualizzare i dettagli nel riquadro di destra.  
  
## <a name="analyzing-conversion-problems-by-using-the-assessment-report"></a>Analisi dei problemi di conversione utilizzando il Report di valutazione  
Il riquadro delle statistiche di conversione sono indicate le statistiche di conversione. Se la percentuale per ogni categoria è inferiore al 100%, è necessario determinare perché la conversione non è riuscita.  
  
**Per visualizzare i problemi di conversione**  
  
1.  Creare il report di valutazione tramite le istruzioni nella procedura precedente.  
  
2.  Nel riquadro sinistro, espandere le cartelle che hanno un'icona di errore rossa o schemi. Continuare a espandere gli elementi fino a quando non si seleziona un singolo elemento che non hanno superato la conversione.  
  
3.  Nella parte superiore del riquadro origine, fare clic su **problema successivo**.  
  
    Il codice problematico è evidenziato come rappresenta il codice correlato nel riquadro di navigazione di destinazione.  
  
4.  Esaminare i messaggi di errore e quindi determinare ciò che si desidera eseguire con l'oggetto che ha causato il problema di conversione:  
  
    -   Aggiornare la sintassi di DB2 in SSMA. È possibile aggiornare la sintassi di routine, funzioni, trigger, funzioni incluse nel pacchetto e nel pacchetto. Per aggiornare la sintassi, selezionare l'oggetto nel riquadro di esplorazione dei metadati di DB2, fare clic su di **SQL** scheda e quindi modificare il codice SQL. Quando si esce dall'elemento, verrà richiesto di salvare l'aggiornamento della sintassi. È possibile visualizzare gli errori segnalati per l'oggetto nella **Report** scheda.  
  
    -   In DB2, è possibile modificare l'oggetto di DB2 per rimuovere o modificare il codice problematico. Per caricare il codice aggiornato in SSMA, è necessario aggiornare i metadati. Per altre informazioni, vedere [la connessione al Database DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/connecting-to-db2-database-db2tosql.md).  
  
    -   È possibile escludere l'oggetto dalla migrazione. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati ed Esplora i metadati di DB2, deselezionare la casella di controllo accanto all'elemento prima di caricare gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e la migrazione dei dati da DB2.  
  
## <a name="next-step"></a>Passaggio successivo  
[Conversione di schemi di DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Database DB2 la migrazione a SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  

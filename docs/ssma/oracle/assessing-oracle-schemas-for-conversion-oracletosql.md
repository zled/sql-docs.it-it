---
title: La valutazione di schemi Oracle per la conversione (OracleToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Analyzing Conversion Problems
ms.assetid: 4de9bcf6-1346-4740-87f9-7f24a8226357
caps.latest.revision: "7"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 1489e4002532d09c0085c64f3aea139f21aab2c1
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="assessing-oracle-schemas-for-conversion-oracletosql"></a>La valutazione di schemi Oracle per la conversione (OracleToSQL)
Prima di caricare gli oggetti e la migrazione dei dati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è necessario determinare come complessa la migrazione sarà e quanto tempo richiederà la migrazione. SSMA è possibile creare un report di valutazione che mostra la percentuale di oggetti che verranno convertiti correttamente. SSMA consente inoltre di visualizzare i problemi specifici che provocano errori di conversione.  
  
## <a name="creating-assessment-reports"></a>Creazione di report di valutazione  
Quando viene creato il report di valutazione, SSMA converte gli oggetti di database Oracle selezionati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sintassi, quindi Mostra i risultati.  
  
**Per creare una relazione di valutazione**  
  
1.  Nel Visualizzatore metadati Oracle, selezionare gli schemi da valutare.  
  
2.  Per omettere i singoli oggetti, deselezionare le caselle di controllo accanto a quelli.  
  
3.  Fare doppio clic su **schemi**, quindi selezionare **crea Report**.  
  
    È inoltre possibile analizzare singoli oggetti destro del mouse su un oggetto e quindi selezionando **crea Report**.  
  
    SSMA viene visualizzato lo stato nella barra di stato nella parte inferiore della finestra. Se il riquadro di Output è visibile, si verifica anche i messaggi nel riquadro di Output.  
  
    Al termine, la valutazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant per Oracle: verrà visualizzata la finestra di Report di valutazione.  
  
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
  
    -   Aggiornare la sintassi di Oracle in SSMA. È possibile aggiornare la sintassi di routine, funzioni, trigger, funzioni incluse nel pacchetto e nel pacchetto. Per aggiornare la sintassi, selezionare l'oggetto nel riquadro di esplorazione dei metadati di Oracle, fare clic su di **SQL** scheda e quindi modificare il codice SQL. Quando si esce dall'elemento, verrà richiesto di salvare l'aggiornamento della sintassi. È possibile visualizzare gli errori segnalati per l'oggetto nella **Report** scheda.  
  
    -   In Oracle, è possibile modificare l'oggetto di Oracle per rimuovere o modificare il codice problematico. Per caricare il codice aggiornato in SSMA, è necessario aggiornare i metadati. Per ulteriori informazioni, vedere [connessione a Oracle Database &#40; OracleToSQL &#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md).  
  
    -   È possibile escludere l'oggetto dalla migrazione. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati ed Esplora i metadati di Oracle, deselezionare la casella di controllo accanto all'elemento prima di caricare gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e la migrazione dei dati da Oracle.  
  
## <a name="next-step"></a>Passaggio successivo  
[Conversione di schemi Oracle &#40; OracleToSQL &#41;](../../ssma/oracle/converting-oracle-schemas-oracletosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database Oracle a SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  

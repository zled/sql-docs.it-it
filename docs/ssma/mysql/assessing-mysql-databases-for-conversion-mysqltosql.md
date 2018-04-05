---
title: Valutazione dei database MySQL per la conversione (MySQLToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Assessment reports
ms.assetid: 2a56a003-3b0f-453a-963c-00c9e40933ec
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 73019709b3ce9b40dc05f678cc64d33305504213
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="assessing-mysql-databases-for-conversion-mysqltosql"></a>Valutazione dei database MySQL per la conversione (MySQLToSQL)
Prima di caricare gli oggetti e la migrazione dei dati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, è necessario determinare come complessa la migrazione sarà e quanto tempo richiederà la migrazione. SSMA è possibile creare un report di valutazione che mostra la percentuale di oggetti che verranno convertiti correttamente. SSMA consente inoltre di visualizzare i problemi specifici che provocano errori di conversione.  
  
## <a name="creating-assessment-reports"></a>Creazione di report di valutazione  
Quando viene creato il report di valutazione, SSMA converte gli oggetti di database MySQL selezionati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o sintassi SQL Azure e quindi Mostra i risultati.  
  
**Per creare una relazione di valutazione**  
  
1.  Nel Visualizzatore metadati MySQL, selezionare gli schemi da valutare.  
  
2.  Per omettere i singoli oggetti, deselezionare le caselle di controllo accanto a quelli.  
  
3.  Fare doppio clic su **schemi**, quindi selezionare **crea Report**.  
  
    Fare doppio clic su un oggetto per analizzare singoli oggetti. Selezionare quindi **crea Report**.  
  
    SSMA viene visualizzato lo stato nella barra di stato nella parte inferiore della finestra. Se il riquadro di Output è visibile, si verifica anche i messaggi nel riquadro di Output.  
  
    Al termine, la valutazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant per MySQL, finestra valutazione Report verranno visualizzati.  
  
## <a name="using-assessment-reports"></a>Utilizzo dei report di valutazione  
La finestra di Report di valutazione contiene tre riquadri:  
  
-   Il riquadro di sinistra contiene la gerarchia di oggetti inclusi nel report di valutazione. È possibile esplorare la gerarchia e selezionare gli oggetti e le categorie di oggetti da visualizzare codice e le statistiche di conversione.  
  
-   Il contenuto del riquadro di destra varia a seconda dell'elemento selezionato nel riquadro a sinistra.  
  
    Se si seleziona un gruppo di oggetti, ad esempio di schema, il riquadro destro contiene un riquadro delle statistiche di conversione e gli oggetti dal riquadro delle categorie. Il riquadro delle statistiche di conversione sono indicate le statistiche di conversione per gli oggetti selezionati. Gli oggetti dal riquadro delle categorie sono indicate le statistiche di conversione per l'oggetto o le categorie di oggetti.  
  
    Se si seleziona una funzione, stored procedure, vista o tabella, riquadro di destra contiene le statistiche, codice sorgente e codice di destinazione.  
  
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
  
4.  Esaminare i messaggi di errore e quindi determinare ciò che si desidera eseguire con l'oggetto che ha causato il problema di conversione.  
  
-   Aggiornare la sintassi di MySQL in SSMA. È possibile aggiornare la sintassi solo per le procedure e funzioni. Per aggiornare la sintassi, selezionare l'oggetto nel riquadro di esplorazione dei metadati di MySQL, fare clic su di **SQL** scheda e quindi modificare il codice SQL. Quando si esce dall'elemento, verrà richiesto di salvare l'aggiornamento della sintassi. È possibile visualizzare gli errori segnalati per l'oggetto nella **Report** scheda.  
  
-   Di MySQL, è possibile modificare l'oggetto di MySQL per rimuovere o modificare il codice problematico. Per caricare il codice aggiornato in SSMA, è necessario aggiornare i metadati. Per ulteriori informazioni, vedere [connessione a MySQL &#40; MySQLToSQL &#41; ](../../ssma/mysql/connecting-to-mysql-mysqltosql.md).  
  
-   È possibile escludere l'oggetto dalla migrazione. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure metadati Explorer e Visualizzatore metadati MySQL, deselezionare la casella di controllo accanto all'elemento prima di caricare gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure e la migrazione dei dati da MySQL.  
  
## <a name="next-step"></a>Passaggio successivo  
[Conversione di database MySQL &#40; MySQLToSQL &#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database MySQL a SQL Server: database SQL di Azure &#40; MySQLToSql &#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  

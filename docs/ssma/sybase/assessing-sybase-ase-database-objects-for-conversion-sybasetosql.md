---
title: Valutare gli oggetti di Database di Sybase ASE per la conversione (SybaseToSQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: eb996b7c-1eef-4f73-b5e6-2fa6faf7336c
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9683542427256511b961ad8f6ffd74af43eb23d5
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="assessing-sybase-ase-database-objects-for-conversion-sybasetosql"></a>Valutare gli oggetti di Sybase ASE Database per la conversione (SybaseToSQL)
Prima di caricare gli oggetti e la migrazione dei dati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, è necessario determinare come complessa la migrazione sarà e quanto tempo richiederà la migrazione. SSMA è possibile creare una relazione di valutazione che mostra la percentuale di oggetti e le procedure che verranno convertite correttamente in [!INCLUDE[tsql](../../includes/tsql_md.md)]. SSMA consente inoltre di visualizzare i problemi specifici che si verificano errori di conversione.  
  
## <a name="creating-assessment-reports"></a>Creazione di report di valutazione  
Quando viene creato il report di valutazione, SSMA converte gli oggetti di database di Sybase Adaptive Server Enterprise (ASE) selezionato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o sintassi SQL Azure e quindi Mostra i risultati.  
  
**Per creare una relazione di valutazione**  
  
1.  In Visualizzatore metadati Sybase, selezionare i database che si desidera valutare.  
  
2.  Per omettere i singoli oggetti, deselezionare le caselle di controllo accanto agli oggetti che non si desidera valutare.  
  
3.  Fare doppio clic su **database**, quindi selezionare **crea Report**.  
  
    È inoltre possibile analizzare singoli oggetti destro del mouse su un oggetto e quindi selezionando **crea Report**.  
  
    SSMA viene visualizzato lo stato nella barra di stato nella parte inferiore della finestra. Se il riquadro di Output è visibile, si verifica anche i messaggi nel riquadro di Output.  
  
    Al termine, la valutazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant per Sybase: verrà visualizzata la finestra di Report di valutazione.  
  
## <a name="using-assessment-reports"></a>Utilizzo dei report di valutazione  
La finestra di Report di valutazione contiene tre riquadri:  
  
-   Il riquadro di sinistra contiene la gerarchia di oggetti inclusi nel report di valutazione. È possibile esplorare la gerarchia e selezionare gli oggetti e le categorie di oggetti per visualizzare le statistiche di conversione e il codice.  
  
-   Il contenuto del riquadro di destra dipende dall'elemento selezionato nel riquadro a sinistra.  
  
    Se si seleziona un gruppo di oggetti, tale schema o una tabella viene selezionato il riquadro di destra contiene un riquadro delle statistiche di conversione e oggetti dal riquadro delle categorie. Il riquadro delle statistiche di conversione sono indicate le statistiche di conversione per gli oggetti selezionati. Gli oggetti dal riquadro delle categorie sono indicate le statistiche di conversione per l'oggetto o le categorie di oggetti.  
  
    Se una stored procedure, una vista o un trigger è selezionata, il riquadro di destra contiene le statistiche, codice sorgente e codice di destinazione.  
  
    -   Nell'area superiore mostra le statistiche generali per l'oggetto. Potrebbe essere necessario espandere **statistiche** per visualizzare queste informazioni.  
  
    -   L'area di origine viene illustrato il codice di origine dell'oggetto selezionato nel riquadro a sinistra. Le aree evidenziate mostrano codice sorgente problematico.  
  
    -   L'area di destinazione Mostra il codice convertito. Testo di colore rosso Mostra messaggi di errore e di codice problematici.  
  
-   Nel riquadro inferiore mostra i messaggi di conversione, raggruppati in base al numero di messaggio. È possibile fare clic su **errori**, **avvisi**, o **Info** per visualizzare le categorie di messaggi e quindi espandere un gruppo di messaggi. Fare clic su un singolo messaggio per selezionare l'oggetto nel riquadro a sinistra e visualizzare i dettagli nel riquadro di destra.  
  
## <a name="analyzing-conversion-problems-using-the-assessment-report"></a>L'analisi dei problemi di conversione utilizzando il Report di valutazione  
I riquadri di statistiche di conversione mostrano le statistiche di conversione. Se la percentuale per ogni categoria è inferiore al 100%, è necessario determinare perché la conversione non è riuscita.  
  
**Per visualizzare i problemi di conversione**  
  
1.  Creare il report di valutazione tramite le istruzioni nella procedura precedente.  
  
2.  Nel riquadro sinistro, espandere le cartelle che hanno un'icona di errore rossa o schemi. Continuare a espandere gli elementi fino a quando non si seleziona un singolo elemento che non hanno superato la conversione.  
  
3.  Nella parte superiore del riquadro origine, fare clic su **problema successivo**.  
  
    Il codice problematico è evidenziato come rappresenta il codice correlato nel riquadro di navigazione di destinazione.  
  
4.  Esaminare i messaggi di errore e quindi determinare ciò che si desidera eseguire con l'oggetto che ha causato il problema di conversione:  
  
    -   Aggiornare la sintassi di base di SSMA. È possibile aggiornare la sintassi solo per le stored procedure e trigger. Per aggiornare la sintassi, selezionare l'oggetto nel riquadro Visualizzatore metadati Sybase, fare clic su di **SQL** scheda e quindi modificare il codice SQL. Quando si esce dall'elemento, verrà richiesto di salvare l'aggiornamento della sintassi. È possibile visualizzare gli errori segnalati per l'oggetto nella **Report** scheda.  
  
    -   In base, è possibile modificare l'oggetto di base per rimuovere o modificare il codice problematico. Per caricare il codice aggiornato in SSMA, è necessario aggiornare i metadati. Per ulteriori informazioni, vedere [connessione per Sybase ASE &#40; SybaseToSQL &#41; ](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
    -   È possibile escludere l'oggetto dalla migrazione. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure metadati Explorer e Visualizzatore metadati Sybase, deselezionare la casella di controllo accanto all'elemento prima di caricare gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure e la migrazione dei dati di base.  
  
## <a name="next-step"></a>Passaggio successivo  
[Conversione di Sybase ASE Database Objects &#40; SybaseToSQL &#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database di Sybase ASE a SQL Server: database SQL di Azure &#40; SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  


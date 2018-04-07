---
title: Valutare gli oggetti di Database SAP ASE per conversione (SybaseToSQL) | Documenti Microsoft
ms.custom: ''
ms.date: 12/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: eb996b7c-1eef-4f73-b5e6-2fa6faf7336c
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 99342797792c8b57eff144e8c5a611bbace2776d
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="assessing-sap-ase-database-objects-for-conversion-sybasetosql"></a>Oggetti di database di valutazione ASE SAP per la conversione (SybaseToSQL)
Prima di caricare gli oggetti e la migrazione dei dati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, è necessario determinare la complessità della migrazione e quanto tempo deve durare. SSMA è possibile creare una relazione di valutazione che mostra la percentuale di oggetti e le procedure che verranno convertite correttamente in [!INCLUDE[tsql](../../includes/tsql_md.md)]. SSMA consente inoltre di visualizzare i problemi specifici che possono causare errori di conversione.  
  
## <a name="create-assessment-reports"></a>Creare report di valutazione  
Quando si crea il report di valutazione, SSMA converte gli oggetti di database SAP Adaptive Server Enterprise (ASE) selezionato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o sintassi SQL di Azure e quindi Mostra i risultati.  
  
**Per creare un report di valutazione**  
  
1.  In Visualizzatore metadati Sybase, selezionare i database che si desidera valutare.  
  
2.  Per omettere i singoli oggetti, deselezionare le caselle di controllo accanto agli oggetti che non si desidera valutare.  
  
3.  Fare doppio clic su **database**, quindi selezionare **crea Report**.  
  
    È inoltre possibile analizzare singoli oggetti destro del mouse su un oggetto e quindi selezionando **crea Report**.  
  
    SSMA Mostra lo stato di avanzamento nella barra di stato nella parte inferiore della finestra. Se il riquadro di Output è visibile, si verifica anche i messaggi correlati.  
  
    Al termine, la valutazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant per Sybase: verrà visualizzata la finestra di Report di valutazione.  
  
## <a name="use-assessment-reports"></a>Utilizzare i report di valutazione  
La finestra di Report di valutazione contiene tre riquadri:  
  
-   Il riquadro di sinistra contiene la gerarchia di oggetti inclusi nel report di valutazione. È possibile esplorare la gerarchia e selezionare gli oggetti e le categorie di oggetto per visualizzare codice e le statistiche di conversione.  
  
-   Il contenuto del riquadro di destra varia in base elemento selezionato nel riquadro a sinistra.  
  
    Se è selezionato un gruppo di oggetti (ad esempio uno schema) o una tabella, il riquadro destro mostra due riquadri. Il **statistiche di conversione** riquadro mostra le statistiche di conversione per gli oggetti selezionati. Il **oggetti in base a categorie** riquadro mostra le statistiche di conversione per l'oggetto o le categorie di oggetti.  
  
    Se una stored procedure, una vista o un trigger è selezionata, il riquadro di destra contiene le statistiche, codice sorgente e codice di destinazione.  
  
    -   Nell'area superiore mostra le statistiche generali per l'oggetto. Potrebbe essere necessario espandere **statistiche** per visualizzare queste informazioni. 
    -   L'area di origine viene illustrato il codice di origine dell'oggetto selezionato nel riquadro a sinistra. Le aree evidenziate mostrano codice sorgente problematico.  
    -   L'area di destinazione Mostra il codice convertito. Testo di colore rosso Mostra messaggi di errore e di codice problematici.  
  
-   Nel riquadro inferiore mostra i messaggi di conversione, raggruppati in base al numero di messaggio. Selezionare **errori**, **avvisi**, o **Info** per visualizzare le categorie di messaggi e quindi espandere un gruppo di messaggi. Fare clic su un singolo messaggio per selezionare l'oggetto nel riquadro sinistro e quindi visualizzare i dettagli nel riquadro di destra.  
  
## <a name="analyze-conversion-problems-by-using-the-assessment-report"></a>Analizzare i problemi di conversione utilizzando il report di valutazione  
Il **riquadri delle statistiche di conversione** Mostra le statistiche di conversione. Se la percentuale per ogni categoria è inferiore al 100%, è necessario determinare perché la conversione non è riuscita.  
  
**Per visualizzare i problemi di conversione**  
  
1.  Creare il report di valutazione tramite le istruzioni nella procedura precedente.  
  
2.  Nel riquadro sinistro, espandere le cartelle che hanno un'icona di errore rossa o schemi. Continuare a espandere gli elementi fino a quando non si seleziona un singolo elemento che non hanno superato la conversione.  
  
3.  Nella parte superiore del riquadro origine, selezionare **problema successivo**.  
    Il codice problematico è evidenziato come rappresenta il codice correlato del **navigazione di destinazione** riquadro.  
  
4.  Esaminare i messaggi di errore e quindi determinare ciò che si desidera eseguire con l'oggetto che ha causato il problema di conversione:  
  
    -   Aggiornare la sintassi di base di SSMA. È possibile aggiornare la sintassi solo per le stored procedure e trigger. Per aggiornare la sintassi, selezionare l'oggetto nel riquadro Visualizzatore metadati Sybase, fare clic su di **SQL** scheda e quindi modificare il codice SQL. Quando si esce dall'elemento, viene chiesto di salvare l'aggiornamento della sintassi. Visualizzare gli errori segnalati per l'oggetto nel **Report** scheda.  
  
    -   In base, è possibile modificare l'oggetto di base per rimuovere o modificare il codice problematico. Per caricare il codice aggiornato in SSMA, è necessario aggiornare i metadati. Per altre informazioni, vedere [ci si connette per Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
    -   È possibile escludere l'oggetto dalla migrazione. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Visualizzatore metadati di SQL Azure e Visualizzatore metadati Sybase, deselezionare la casella di controllo accanto all'elemento prima di caricare gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure e la migrazione dei dati di base.
  
## <a name="next-steps"></a>Passaggi successivi  
[Conversione di oggetti di Database ASE SAP &#40;SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database SAP ASE a SQL Server - database SQL di Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  

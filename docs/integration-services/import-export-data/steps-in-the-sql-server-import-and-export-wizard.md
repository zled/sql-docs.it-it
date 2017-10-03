---
title: I passaggi in SQL Server importazione / esportazione guidata | Documenti Microsoft
ms.custom: 
ms.date: 02/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 816fb1bd-7bb9-450d-ad65-e4c2d02eaff8
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 22d1f4b78fadab6d7b6659104b54a564f11da308
ms.contentlocale: it-it
ms.lasthandoff: 09/27/2017

---
# <a name="steps-in-the-sql-server-import-and-export-wizard"></a>Importazione / esportazione guidata di passaggi in SQL Server
In questo argomento viene descritta la sequenza di passaggi per l'importazione ed esportazione di dati con SQL Server di importazione / esportazione guidata. Contiene inoltre collegamenti a singole pagine della documentazione che descrivono ogni pagina o la finestra di dialogo che viene visualizzato nella procedura guidata.

Questo argomento viene descritto solo il **passaggi** nella procedura guidata. Se si sta cercando un altro elemento, vedere [correlati e i contenuti](#related).

## <a name="steps-for-importing-and-exporting-data"></a>Passaggi per importare ed esportare dati  
 La tabella seguente elenca i passaggi necessari per l'importazione e l'esportazione di dati e le pagine corrispondenti della procedura guidata. A seconda delle opzioni selezionate nella procedura guidata, in genere non trovi tutte queste pagine.  

Per un rapido controllo le schermate visualizzate diverse in una sessione tipica, esaminiamo questo semplice esempio end-to-end in una singola pagina - [iniziare con questo semplice esempio di importazione / esportazione guidata](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md).

|Passaggio|Pagine della procedura guidata|  
|----------|------------------|  
|**Pagina iniziale**<br />Non è necessario eseguire alcuna operazione in questa pagina.|[Importazione/Esportazione guidata SQL Server](../../integration-services/import-export-data/welcome-to-sql-server-import-and-export-wizard.md)|  
|**Selezionare l'origine** dei dati.|[Scegliere un'origine dati](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)|  
|**Selezionare la destinazione** dei dati.|[Scegliere una destinazione](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)|  
|**Configurare la destinazione**. (passaggi facoltativi)<br /><br /> -   Creare un nuovo database di destinazione.<br />-   Se si stanno copiando dati in un file di testo, configurare impostazioni aggiuntive.|[Creazione di Database](../../integration-services/import-export-data/create-database-sql-server-import-and-export-wizard.md)<br /><br />[Configurare destinazione File Flat](../../integration-services/import-export-data/configure-flat-file-destination-sql-server-import-and-export-wizard.md)|  
|**Specificare gli elementi da copiare.**|[Impostazione copia tabella o Query](../../integration-services/import-export-data/specify-table-copy-or-query-sql-server-import-and-export-wizard.md)<br /><br />[Selezionare le tabelle di origine e le viste](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md)<br /><br />[Specificare una Query di origine](../../integration-services/import-export-data/provide-a-source-query-sql-server-import-and-export-wizard.md)|  
|**Configurare l'operazione di copia**. (passaggi facoltativi)<br /><br /> -   Creare una nuova tabella di destinazione.<br />-Decidere cosa fare se la procedura guidata non riesce a eseguire il mapping di tipi di dati tra l'origine e la destinazione selezionata.<br />-   Rivedere i mapping a livello di colonne tra l'origine e la destinazione.<br />-   Gestire i problemi mediante la conversione dei tipi di dati tra l'origine e la destinazione.<br />-   Visualizzare in anteprima i dati da copiare.|[Istruzione SQL Create Table](../../integration-services/import-export-data/create-table-sql-statement-sql-server-import-and-export-wizard.md)<br /><br />[Converti tipi senza i controlli di conversione](../../integration-services/import-export-data/convert-types-without-conversion-checking-sql-server-import-and-export-wizard.md)<br /><br />[Mapping delle colonne](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md)<br /><br />[Esaminare i Mapping dei tipi di dati](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md)<br /><br />[Finestra di dialogo Dettagli conversione colonna](../../integration-services/import-export-data/column-conversion-details-dialog-box-sql-server-import-and-export-wizard.md)<br /><br />[Finestra di dialogo Anteprima dati](../../integration-services/import-export-data/preview-data-dialog-box-sql-server-import-and-export-wizard.md)|  
|**Copiare i dati.**<br /><br /> Facoltativamente, è possibile salvare le impostazioni come un pacchetto di SQL Server Integration Services (SSIS).|[Salvare ed eseguire pacchetti](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md)<br /><br />[Salva pacchetto SSIS](../../integration-services/import-export-data/save-ssis-package-sql-server-import-and-export-wizard.md)<br /><br />[Completare la procedura guidata](../../integration-services/import-export-data/complete-the-wizard-sql-server-import-and-export-wizard.md)<br /><br />[Operazione](../../integration-services/import-export-data/performing-operation-sql-server-import-and-export-wizard.md)|  

> [!TIP]
> Premere il tasto F1 da qualsiasi pagina o finestra di dialogo della procedura guidata per visualizzare la documentazione relativa alla pagina corrente.

## <a name="related"></a>Contenuto e le attività correlate  
Ecco alcune semplici attività.
-   **Vedere un esempio semplice di funzionamento della procedura guidata.**

    -   **Se si preferisce visualizzare schermate.** Esaminiamo questo semplice esempio end-to-end in una singola pagina - [iniziare con questo semplice esempio di importazione / esportazione guidata](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md).

    -   **Se si preferisce guardare un video.** Guardare questo video di quattro minuti dal YouTube che illustra la procedura guidata e viene spiegato chiaramente in modo semplice e come esportare i dati in Excel - [utilizzando SQL Server di importazione / esportazione guidata per l'esportazione in Excel](https://go.microsoft.com/fwlink/?linkid=829049).

-   **Ulteriori informazioni sul funzionamento della procedura guidata.**

    -   **Ulteriori informazioni sulla procedura guidata.** Per una panoramica della procedura guidata, vedere [Importare ed esportare dati con l'Importazione/Esportazione guidata SQL Server](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).

    -   **Informazioni su come connettersi a origini dati e destinazioni.** Se si sta cercando informazioni su come connettersi ai dati, selezionare la pagina desiderata dall'elenco, [connessione a origini dati con SQL Server di importazione / esportazione guidata](../../integration-services/import-export-data/connect-to-data-sources-with-the-sql-server-import-and-export-wizard.md). È una pagina separata della documentazione per ognuna delle diverse origini dati di uso comune. 

-   **Avviare la procedura guidata.** Se si è pronti per eseguire la procedura guidata e servono solo le istruzioni per iniziare, vedere [Avviare l'Importazione/Esportazione guidata SQL Server](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md).

-     **Ottenere la procedura guidata.** Se si vuole eseguire la procedura guidata, ma [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è disponibile nel computer, è possibile installare l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installando SQL Server Data Tools (SSDT). Per altre informazioni, vedere [Scaricare SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx).




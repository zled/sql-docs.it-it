---
title: 'Esercitazione: Utilizzo dell''origine OData | Documenti Microsoft'
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c64cf8b-5edb-48df-8ffe-697096258f71
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: ee79d0f1b31963b7d13aa07bf4603246139c3a7c
ms.openlocfilehash: cbdc4a2e0719e65e378d232c5abcb5404e8342f1
ms.contentlocale: it-it
ms.lasthandoff: 08/23/2017

---
# <a name="tutorial-using-the-odata-source"></a>Esercitazione: utilizzo dell'origine OData
  In questa esercitazione viene eseguito il processo per estrarre la raccolta **Dipendenti** del servizio **Northwind** OData di esempio (http://services.odata.org/V3/Northwind/Northwind.svc/) e caricarla in un file flat.  
  
## <a name="1-create-an-integration-services-project"></a>1. Creare un progetto di Integration Services  
  
1.  Avviare **SQL Server Data Tools** o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
2.  Fare clic su **Nuovo**dal menu **File**, quindi scegliere **Progetto**.  
  
3.  Nella finestra di dialogo **Nuovo progetto** espandere **Installato**, **Modelli**, **Business Intelligence**, quindi scegliere **Integration Services**.  
  
4.  Selezionare **Progetto di Integration Services** come tipo di progetto.  
  
5.  Immettere un **nome** e selezionare un **percorso** per il progetto, quindi fare clic su **OK**.  
  
## <a name="2-add-and-configure-an-odata-source"></a>2. Aggiungere e configurare un'origine OData 
  
1.  Trascinare un'**Attività Flusso di dati** da **Casella degli strumenti SSIS** all'area di progettazione del flusso di controllo del pacchetto SSIS.  
  
2.  Fare clic su di **del flusso di dati** scheda o fare doppio clic su di **attività flusso di dati** per aprire l'area di progettazione del flusso di dati.  
  
3.  Trascinare **Origine Odata** dal gruppo **Comune** in **Casella degli strumenti SSIS**.
  
4.  Fare doppio clic su di **origine OData** componente per avviare il **Editor origine OData** la finestra di dialogo.  
  
5.  Fare clic su **Nuovo…** per aggiungere una nuova gestione connessione OData.  
  
6.  Immettere l'URL del servizio OData in **percorso documento di servizio**. Questo URL può essere l'URL del documento di servizio o a un feed specifico o l'entità. Ai fini di questa esercitazione, immettere l'URL del documento di servizio: [http://services.odata.org/V3/Northwind/Northwind.svc/](http://services.odata.org/V3/Northwind/Northwind.svc/).  
  
7.  Verificare che sia selezionato **Autenticazione di Windows** come **autenticazione** da utilizzare per accedere al servizio OData. **Autenticazione di Windows** è selezionato per impostazione predefinita.  
  
8.  Fare clic su **Test connessione** per testare la connessione, fare clic su **OK** per completare la creazione di un'istanza della gestione connessione OData.  
  
9. Nella finestra di dialogo **Editor origine OData** , verificare che **Raccolta** sia selezionato per l'opzione **Utilizza raccolta in percorso risorse** .  
  
10. Dal **raccolta** elenco a discesa, seleziona **dipendenti**.  
  
11. Immettere tutti i filtri o le opzioni query OData aggiuntive per **Opzioni query**. Ad esempio, `$orderby=CompanyName&$top=100`. Ai fini di questa esercitazione, immettere `$top=5`.  
  
12. Fare clic su **Anteprima** per visualizzare un'anteprima dei dati.  
  
13. Fare clic su **Colonne** nel riquadro di navigazione sinistro per passare alla pagina **Colonne** .  
  
14. Scegliere **EmployeeID**, **FirstName**e **LastName** da **Colonne esterne disponibili** selezionando le caselle di controllo.  
  
15. Fare clic su **OK** per chiudere la finestra di dialogo **Editor origine OData** .  
  
## <a name="3-add-and-configure-a-flat-file-destination"></a>3. Aggiungere e configurare una destinazione File Flat
  
1.  Trascinare una **Destinazione file flat** dalla **casella degli strumenti SSIS** all'area di progettazione del flusso di dati sotto il componente **Origine Odata**.  
  
2.  Connettere il componente **Origine Odata** al componente **Destinazione file flat** utilizzando la freccia blu.  
  
3.  Fare doppio clic su **Destinazione file flat**. Viene visualizzata la finestra di dialogo **Editor destinazione file flat** .  
  
4.  Nella finestra di dialogo **Editor destinazione file flat** fare clic su **Nuovo** per creare una nuova gestione connessione file flat.  
  
5.  Nella finestra di dialogo **Formato file flat** selezionare **Delimitato**. Verranno visualizzate le **Editor gestione connessione File Flat** la finestra di dialogo.  
  
6.  Nel **Editor gestione connessione File Flat** nella finestra di dialogo per la **nome File**, immettere `c:\Employees.txt`.  
  
7.  Fare clic su **Colonne**nel pannello di navigazione sinistro. In questa pagina è possibile visualizzare l'anteprima dei dati.  
  
8.  Fare clic su OK per chiudere la finestra di dialogo **Editor gestione connessione file flat** .  
  
9. Nella finestra di dialogo **Editor destinazione file flat** fare clic su **Mapping** nel riquadro di navigazione sinistro. Controllare i mapping.  
  
10. Fare clic su OK per chiudere la finestra di dialogo **Editor destinazione file flat** .  

## <a name="4-run-the-package"></a>4. Eseguire il pacchetto
Eseguire il pacchetto SSIS. Verificare che il file di output viene creato con l'ID, il nome e cognome di 5 dipendenti dal OData feed.
  
  


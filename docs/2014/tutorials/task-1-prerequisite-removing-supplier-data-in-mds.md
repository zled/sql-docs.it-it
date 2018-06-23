---
title: 'Attività 1 (prerequisito): Rimozione dei dati fornitore in MDS | Documenti Microsoft'
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
ms.assetid: 6f0a4287-7fd4-4f18-b7e4-a5191a9d4a3c
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1189c064ec1a55da1c77837d1533855266ed4274
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171134"
---
# <a name="task-1-prerequisite-removing-supplier-data-in-mds"></a>Attività 1 (prerequisito): Rimozione dei dati fornitore in MDS
  In questa attività vengono rimossi i dati fornitore archiviati in MDS. Caricato i dati manualmente tramite **componente aggiuntivo MDS per Excel** nella lezione precedente. Tramite il pacchetto SSIS creato durante questa lezione i dati vengono caricati automaticamente in MDS. Pertanto, prima di testare il pacchetto SSIS, è necessario rimuovere i dati fornitore da MDS, la gerarchia derivata, le entità Supplier e State e creare l'entità Supplier senza alcun dato.  
  
1.  Avviare **gestione dati Master** passando alla **http://localhost/MDS** o il sito Web e l'applicazione è specificato quando la configurazione di MDS. Se incluso il **gestione dati Master** aperto, fare clic su **SQL Server 2012 Master Data Services** nella parte superiore per passare al **home page di**.  
  
2.  Fare clic su **Amministrazione sistema** nel **le attività amministrative** sezione.  
  
3.  Posizionare il mouse sopra **Manage** dal menu e fare clic su **gerarchie derivate**. È necessario eliminare la gerarchia derivata **SuppliersInState** prima di eliminare le entità nel **Suppliers** modello.  
  
4.  Selezionare **SuppliersInState** dal **gerarchia derivata** elenco e fare clic su **X (Elimina)** pulsante sulla barra degli strumenti.  
  
5.  Fare clic su **OK** per confermare l'eliminazione.  
  
6.  Posizionare il mouse sopra **Manage** dal menu e fare clic su **entità**.  
  
7.  Fare clic su **fornitore** e fare clic su **Elimina (X)** pulsante sulla barra degli strumenti per eliminare l'entità. Fare clic su **OK** nelle finestre di messaggio.  
  
8.  Ripetere il passaggio precedente per eliminare **stato** entità.  
  
9. Non chiudere **gestione dati Master**.  
  
10. Passare alla finestra di Excel contenente **Cleansed and Matched Suppliers. xls** file aperto. Passare il **Sheet1** scheda nella parte inferiore.  
  
11. Selezionare solo il **prima riga con intestazioni**. Non selezionare nessun'altra riga. Si desidera creare entità basate sulle colonne di Excel senza caricare alcun dato. Pertanto, selezionare solo la prima riga con le intestazioni.  
  
12. Fare clic su **dati Master** nella barra dei menu.  
  
13. Fare clic su **Crea entità** dalla barra multifunzione.  
  
14. In **Gestisci connessioni** finestra di dialogo, se non viene visualizzata la connessione a **server MDS locale** sotto **connessioni esistenti**, eseguire le operazioni seguenti:  
  
    1.  Selezionare **creare una nuova connessione**, fare clic su **New** pulsante.  
  
    2.  Nella finestra di dialogo Aggiungi nuova connessione, digitare **Server MDS locale** per **descrizione** e **http://localhost/MDS** per **indirizzo server MDS**, Fare clic su **OK** per chiudere la finestra di dialogo.  
  
15. In **Gestisci connessioni** finestra di dialogo **Server MDS locale** (http://localhost/MDS), fare clic su **Test** per testare la connessione. Fare clic su **OK** nella finestra di messaggio.  
  
16. Fare clic su **Connetti** per stabilire una connessione al server MDS.  
  
17. Nel **Crea entità** dialogo casella, eseguire le operazioni seguenti:  
  
    1.  Verificare che **intervallo** è impostata su **$1: $1**.  
  
    2.  Selezionare **Suppliers** per **modello**.  
  
    3.  Selezionare **VERSION_1** per **versione**.  
  
    4.  Tipo di **fornitore** per **Nome nuova entità**.  
  
    5.  Selezionare **SupplierID** per **codice**.  
  
    6.  Selezionare **Supplier Name** per **nome**.  
  
    7.  Fare clic su **OK** per creare l'entità e chiudere la finestra di dialogo.  
  
18. Chiudi **Excel** e **non si salva** il file.  
  
19. In **gestione dati Master**, aggiornare il browser internet e verificare che **fornitore** entità viene visualizzata nell'elenco.  
  
20. Passare il **homepage** facendo clic su **SQL Server 2012 Master Data Services** nella parte superiore.  
  
21. Verificare che **Suppliers** modello è selezionato per **modello** e **VERSION_1** sia selezionata per **versione**.  
  
22. Fare clic su **Esplora**. Si noti che il **fornitore** entità con tutti gli attributi viene creato con **senza valori**.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 2 &#40;facoltativo&#41;: creazione di viste sottoscrizioni MDS tramite Gestione dati Master](../../2014/tutorials/task-2-optional-creating-a-mds-subscription-view-using-master-data-manager.md)  
  
  
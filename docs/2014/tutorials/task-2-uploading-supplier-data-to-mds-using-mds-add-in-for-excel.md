---
title: 'Attività 2: Caricamento dei dati fornitore in MDS utilizzando il componente aggiuntivo MDS per Excel | Documenti Microsoft'
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
ms.assetid: 598deb57-e0cc-4e0a-aeb1-94432c094c67
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1831fc9ea79027e24d752d05e3b50d3a58d6e06f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062780"
---
# <a name="task-2-uploading-supplier-data-to-mds-using-mds-add-in-for-excel"></a>Attività 2: Caricamento dei dati fornitore in MDS utilizzando il componente aggiuntivo MDS per excel
  In questa attività si pubblicano i dati puliti e fornitore **MDS** usando la **il componente aggiuntivo MDS per Excel**. Si crea un'entità denominata **fornitore** nel **Suppliers** modello creato nella lezione precedente. All'entità sarà associato un attributo per ogni colonna nel file di Excel. Gli attributi Name e Code dell'entità Supplier corrispondono per la **SupplierID** e **Supplier Name** colonne in Excel.  
  
1.  Aprire **puliti e Matched Suppliers. xls** in **Excel**.  
  
2.  Premere **CTRL + A** per selezionare tutti i dati. Si tratta **importanti** di selezionare tutti i dati nel foglio di calcolo.  
  
3.  Fare clic su **dati Master** nella barra dei menu.  
  
4.  Fare clic su **Crea entità** pulsante della barra multifunzione.  
  
     ![Excel - scheda dati Master - pulsante Crea entità](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-01.jpg "Excel - scheda dati Master - pulsante Crea entità")  
  
5.  In **Gestisci connessioni** finestra di dialogo, se non viene visualizzata la connessione a **server MDS locale** sotto **connessioni esistenti**, eseguire le operazioni seguenti:  
  
    1.  Selezionare **creare una nuova connessione**, fare clic su **New** pulsante.  
  
    2.  Nel **Aggiungi nuova connessione** finestra di dialogo, digitare **Server MDS locale** per **descrizione** e **http://localhost/MDS** per  **Indirizzo server MDS**, fare clic su **OK** per chiudere la finestra di dialogo.  
  
6.  In **Gestisci connessioni** finestra di dialogo **Server MDS locale** (http://localhost/MDS), fare clic su **Test** per testare la connessione. Fare clic su **OK** nella finestra di messaggio.  
  
7.  Fare clic su **Connetti** per la connessione al server MDS.  
  
8.  Nel **Crea entità** finestra di dialogo **Suppliers** per il **modello**.  
  
9. Assicurarsi che **VERSION_1** sia selezionata per **versione**.  
  
10. Immettere **fornitore** per **Nome nuova entità**.  
  
11. Selezionare **SupplierID** per **la colonna che contiene un identificatore univoco** campo (è anche possibile generare un codice automaticamente). Si esegue il mapping essenzialmente il **SupplierID** colonna **Excel** per il **codice** attributo di **fornitore** entità.  
  
12. Selezionare **Supplier Name** per **la colonna che contiene i nomi** campo. Essenzialmente si esegue il mapping di **Supplier Name** colonna **Excel** per il **nome** attributo del **fornitore** entità. Il **codice** e **nome** gli attributi sono attributi obbligatori per un'entità in MDS.  
  
     ![Finestra di dialogo entità crea](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-02.jpg "creare entità, finestra di dialogo")  
  
13. Fare clic su **OK** per creare l'entità in MDS, pubblicare i dati master all'entità e chiudere **Crea entità** finestra di dialogo.  
  
14. A questo punto, verrà visualizzato un nuovo foglio denominato **fornitore**, ovvero il nome dell'entità, aggiunto al foglio di calcolo di Excel ed nella parte superiore del foglio di lavoro è necessario verificare che il foglio di lavoro sia connesso al server MDS. Si noti che il foglio di lavoro originale (intitolato **Sheet1**) esiste ancora.  
  
     ![Excel - schede fornitore e Foglio1](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-03.jpg "Excel - schede fornitore e Foglio1")  
  
     ![Excel - visualizzazione Dettagli connessione MDS](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-04.jpg "Excel - visualizzazione Dettagli connessione MDS")  
  
15. Mantenere **Excel** aprire.  
  
## <a name="next-task"></a>Attività successiva  
 [Attività 3: Verifica dei dati in Gestione dati Master](../../2014/tutorials/task-3-verifying-the-data-in-master-data-manager.md)  
  
  
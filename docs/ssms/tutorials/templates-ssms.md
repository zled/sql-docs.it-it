---
Title: 'Tutorial: Using Templates in SQL Server Management Studio'
description: Esercitazione per l'uso di modelli in SSMS. ,
keywords: SQL Server, SSMS, SQL Server Management Studio, Modelli
author: MashaMSFT
ms.author: mathoma
ms.date: 03/13/2018
ms.topic: Tutorial
ms.suite: sql
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
helpviewer_keywords:
- templates [SQL Server], SQL Server Management Studio
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- SQL Server Management Studio [SQL Server], tutorials
- scripts [SQL Server], SQL Server Management Studio
ms.openlocfilehash: a01586f4ab3d002e33b7679f6fe2e5a165f260e1
ms.sourcegitcommit: ccb05cb5a4cccaf7ffa9e85a4684fa583bab914e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2018
---
# <a name="tutorial-using-templates-within-sql-server-management-studio"></a>Esercitazione: Uso di modelli in SQL Server Management Studio
Questa esercitazione illustra i modelli predefiniti di Transact-SQL (T-SQL) che sono disponibili in SQL Server Management Studio (SSMS). In questo articolo vengono illustrate le operazioni seguenti:

> [!div class="checklist"]
> * Usare il visualizzatore modelli per generare script T-SQL
> * Modificare un modello esistente 
> * Individuare i modelli su disco
> * Creare un nuovo modello
   

## <a name="prerequisites"></a>Prerequisites
Per completare questa esercitazione, sono necessari SQL Server Management Studio e l'accesso a SQL Server. 

- Installare [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).
- Installare [SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads).

 

## <a name="using-the-template-browser"></a>Uso del visualizzatore modelli
In questa sezione si apprenderà come individuare e usare il **Visualizzatore modelli**. 

1. Avviare SQL Server Management Studio.
2. Dal menu **Visualizza** > **Visualizzatore modelli** (CTRL+ALT+T): 

    ![Visualizzatore modelli](media/templates-ssms/templatebrowser.png)
    - È anche possibile visualizzare i modelli usati di recente nella parte inferiore di **Visualizzatore modelli**.

3. Espandere il nodo di interesse > fare clic con il pulsante destro del mouse sul modello > Apri:

    ![Aprire un modello](media/templates-ssms/opentemplate.png)
    - In alternativa, fare doppio clic sul modello.

4. Viene avviata una nuova finestra di query con l'istruzione T-SQL già popolata. 
5. Modificare il modello in base alle esigenze e selezionare **Esegui** per eseguire la query:
    
    ![Creare il modello di database](media/templates-ssms/createdbtemplate.png)


## <a name="edit-an-existing-template"></a>Modificare un modello esistente
È anche possibile modificare i modelli esistenti all'interno del **Visualizzatore modelli**.  

1. Individuare il modello di interesse nel **Visualizzatore modelli**.
2. Fare clic con il pulsante destro del mouse sul modello > **Modifica**:

    ![Modificare il modello](media/templates-ssms/edittemplate.png)

3. Apportare le modifiche desiderate nella finestra di query che viene aperta.
4. Salvare il modello selezionando **File** > **Salva** (CTRL+S).
5. Chiudere la finestra di query.
6. Riaprire il modello che è stato salvato > tutte le nuove modifiche dovrebbero essere presenti.
 

## <a name="locate-the-templates-on-disk"></a>Individuare i modelli su disco
Una volta aperto un modello, è possibile individuarlo sul disco.

1. Selezionare un modello in **Visualizzatore modelli** > **Modifica**.
2. Fare clic con il pulsante destro del mouse sul **titolo della query** > **Open Containing Folder** (Apri cartella superiore). In questo modo viene aperto Esplora risorse dove sono visualizzati i modelli archiviati su disco: 

    ![Modelli su disco](media/templates-ssms/templatesondisk.png)
  

## <a name="create-a-new-template"></a>Creare un nuovo modello
In **Visualizzatore modelli** è anche possibile creare nuovi modelli. I passaggi seguenti illustrano come creare una nuova cartella e quindi creare un nuovo modello all'interno di tale cartella. Tuttavia, con questi passaggi è possibile creare anche un modello personalizzato all'interno di cartelle esistenti. 

1. Aprire **Visualizzatore modelli**.
2. Fare clic con il pulsante destro del mouse su Modelli di SQL Server > **Nuovo** > **Cartella**.
3. Denominare la cartella **Modelli personalizzati**:

    ![Creazione di modelli personalizzati](media/templates-ssms/creatingcustomtemplate.png)

4. Fare clic con il pulsante destro del mouse sulla cartella **Modelli personalizzati** appena creata > **Nuovo** > **Modello** > denominare il modello:
 
    ![Creare modelli personalizzati](media/templates-ssms/createnewtemplate.png)
   
5. Fare clic con il pulsante destro del mouse sul modello appena creato > **Modifica**. Viene aperta una **nuova finestra di query**.
6. Digitare il testo T-SQL che si vuole salvare. 
7. Salvare il file selezionando il menu **File** > **Salva**.
8. Chiudere la **finestra di query** esistente e aprire il nuovo modello personalizzato. 

    

## <a name="next-steps"></a>Passaggi successivi
Nell'articolo successivo verranno offerti alcuni suggerimenti e consigli aggiuntivi per l'uso di SQL Server Management Studio. 

Per altre informazioni, vedere l'articolo successivo
> [!div class="nextstepaction"]
> [Pulsante passaggi successivi](ssms-tricks.md)

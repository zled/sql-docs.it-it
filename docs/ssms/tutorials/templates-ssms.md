---
Title: 'Tutorial: Using templates in SQL Server Management Studio'
description: Esercitazione per l'uso di modelli in SSMS.
keywords: SQL Server, SSMS, SQL Server Management Studio, Modelli
author: MashaMSFT
ms.author: mathoma
ms.date: 03/13/2018
ms.topic: Tutorial
ms.prod: sql
ms.technology: ssms
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
ms.openlocfilehash: 4d3f2de58bdbfb4f476710bb9bb629dcac3db940
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47670039"
---
# <a name="tutorial-using-templates-in-sql-server-management-studio"></a>Esercitazione: Uso di modelli in SQL Server Management Studio
Questa esercitazione illustra i modelli predefiniti di Transact-SQL (T-SQL) che sono disponibili in SQL Server Management Studio (SSMS). In questo articolo vengono illustrate le operazioni seguenti:

> [!div class="checklist"]
> * Usare il visualizzatore modelli per generare script T-SQL
> * Modificare un modello esistente 
> * Individuare i modelli su disco
> * Creare un nuovo modello
   

## <a name="prerequisites"></a>Prerequisites
Per completare questa esercitazione, è necessario SQL Server Management Studio e l'accesso a un server SQL. 

- Installare [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Installare [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).

 

## <a name="use-template-browser"></a>Usare il visualizzatore modelli
Questa sezione illustra come individuare e usare il visualizzatore modelli. 

1. Aprire SQL Server Management Studio.
2. Nel menu **Visualizza** selezionare **Visualizzatore modelli** (CTRL+ALT+T): 

    ![Aprire il visualizzatore modelli](media/templates-ssms/templatebrowser.png)
    
    È possibile visualizzare i modelli usati di recente nella parte inferiore del visualizzatore modelli.

3. Espandere il nodo desiderato. Fare clic con il pulsante destro sul modello e quindi selezionare **Apri**:

    ![Aprire un modello](media/templates-ssms/opentemplate.png)
    
    È anche possibile fare doppio clic sul nome del modello per aprirlo.

4. Viene visualizzata una nuova finestra di query. Lo script T-SQL è già popolato. 
5. Modificare il modello in base alle esigenze e selezionare **Esegui** per eseguire la query:
    
    ![Creare un modello di database](media/templates-ssms/createdbtemplate.png)


## <a name="edit-an-existing-template"></a>Modificare un modello esistente
È anche possibile modificare i modelli esistenti nel visualizzatore modelli.  

1. Nel visualizzatore modelli passare al modello da usare.
2. Fare clic con il pulsante destro del mouse sul modello e quindi scegliere **Modifica**:

    ![Modificare un modello](media/templates-ssms/edittemplate.png)

3. Nella finestra di query aperta apportare le modifiche desiderate.
4. Per salvare il modello, selezionare **File** > **Salva** (CTRL+S).
5. Chiudere la finestra di query.
6. Riaprire il modello. Vengono visualizzate le modifiche apportate.
 

## <a name="locate-templates-on-disk"></a>Individuare i modelli su disco
Quando un modello è aperto, è possibile individuare i modelli che si trovano su disco.

1. Nel visualizzatore modelli selezionare un modello e quindi scegliere **Modifica**.
2. Fare clic con il pulsante destro del mouse su **Titolo query**, quindi selezionare **Apri cartella superiore**. I modelli archiviati su disco vengono visualizzati in Esplora risorse: 

   ![Modelli su disco](media/templates-ssms/templatesondisk.png)
  

## <a name="create-a-new-template"></a>Creare un nuovo modello
È anche possibile creare un nuovo modello nel visualizzatore modelli. La procedura seguente illustra come creare una nuova cartella e quindi creare un nuovo modello nella cartella. È anche possibile seguire la procedura per creare un modello personalizzato in una cartella esistente. 

1. Aprire il visualizzatore modelli.
2. Fare clic con il pulsante destro del mouse su **Modelli di SQL Server** e quindi selezionare **Nuovo** > **Cartella**.
3. Denominare la cartella **Modelli personalizzati**:

    ![Creare una cartella di modelli personalizzati](media/templates-ssms/creatingcustomtemplate.png)

4. Fare clic con il pulsante destro del mouse sulla cartella Modelli personalizzati appena creata e quindi selezionare **Nuovo** > **Modello**. Immettere un nome per il modello:
 
    ![Creare un modello personalizzato](media/templates-ssms/createnewtemplate.png)
   
5. Fare clic con il pulsante destro del mouse sul modello creato e quindi scegliere **Modifica**. Viene visualizzata la nuova finestra di query.
6. Immettere il testo T-SQL che si vuole salvare. 
7. Scegliere **Salva** dal menu **File**.
8. Chiudere la finestra di query esistente e aprire il nuovo modello personalizzato. 

    

## <a name="next-steps"></a>Passaggi successivi
L'articolo successivo offre suggerimenti e consigli aggiuntivi per l'uso di SQL Server Management Studio. 

> [!div class="nextstepaction"]
> [Suggerimenti e consigli per l'uso di SSMS](ssms-tricks.md)

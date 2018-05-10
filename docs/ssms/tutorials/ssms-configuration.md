---
Title: 'Tutorial: SQL Server Management Studio Components and Configuration'
description: Esercitazione che descrive i componenti e le opzioni di configurazione di base per l'ambiente di SQL Server Management Studio.
keywords: SQL Server, SSMS, SQL Server Management Studio
author: MashaMSFT
ms.author: mathoma
ms.date: 03/16/2018
ms.topic: Tutorial
ms.suite: sql
ms.prod: sql
ms.technology: ssms
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
ms.openlocfilehash: b2c850ac32aebf78441234327ec33b6223dc447b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="tutorial-sql-server-management-studio-components-and-configuration"></a>Esercitazione: Componenti e configurazione di SQL Server Management Studio
In questa esercitazione vengono descritti i vari componenti finestra all'interno di SQL Server Management Studio (SSMS) e alcune opzioni di configurazione di base per l'area di lavoro. In questo articolo viene illustrato quanto segue: 

> [!div class="checklist"]
> * I diversi componenti che costituiscono l'ambiente di SSMS
> * Modifica del layout ambiente e reimpostazione dei valori predefiniti
> * Ingrandimento dell'editor di query
> * Modifica del tipo di carattere 
> * Configurazione delle opzioni di avvio 
> * Reimpostazione della configurazione ai valori predefiniti 

## <a name="prerequisites"></a>Prerequisites
Per completare questa esercitazione è necessario avere SQL Server Management Studio.  

- Installare [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="sql-server-management-studio-components"></a>Componenti di SQL Server Management Studio
In questa sezione vengono illustrati i vari componenti finestra disponibili nell'area di lavoro e il loro scopo. 

- Ogni componente finestra può essere chiuso selezionando la X nell'angolo della barra del titolo e quindi riaperto dall'elenco a discesa **Visualizza** nel menu principale. 

    ![Menu Visualizza](media/ssms-configuration/viewmenu.png)

- **Esplora oggetti** (F8): Esplora oggetti è una visualizzazione struttura ad albero di tutti gli oggetti di database nel server. Sono inclusi i database del motore di database di SQL Server, Analysis Services, Reporting Services e Integration Services. Esplora oggetti contiene informazioni su tutti i server ai quali è connesso. 
    
    ![Esplora oggetti](media/ssms-configuration/objectexplorer.png)
- **Finestra di query** (CTRL+N): dopo aver fatto clic su **Nuova query**, in questa finestra sarà possibile digitare le query Transact-SQL (T-SQL). Qui sono disponibili anche i risultati delle query.
    
    ![Finestra Nuova query](media/ssms-configuration/newquery.png)

- **Proprietà** (F4): questa finestra di dialogo viene visualizzata quando la **finestra di query** è aperta e include le proprietà di base della query. Ad esempio, visualizza l'orario in cui è stata avviata una query, il numero di righe restituite e i dettagli di connessione.  

    ![Proprietà](media/ssms-configuration/properties.png)

- **Visualizzatore modelli** (CTRL+ALT+T): nel Visualizzatore modelli sono presenti numerosi modelli T-SQL predefiniti. Questi modelli consentono di eseguire varie funzioni quali la creazione o il backup di database. 

    ![Visualizzatore modelli](media/ssms-configuration/templates.png)

- **Dettagli Esplora oggetti**(F7): si tratta di una vista più granulare rispetto a Esplora oggetti che consente di modificare più oggetti contemporaneamente. Ad esempio, la finestra Dettagli Esplora oggetti consente di selezionare più database contemporaneamente e di eliminarli o includerli in uno script. 

    ![Visualizza](media/ssms-configuration/objectexplorerdetails.PNG) 
 

    

## <a name="change-the-environmental-layout"></a>Modificare il layout di ambiente 
In questa sezione viene illustrata la modifica del layout di ambiente, ad esempio lo spostamento delle varie finestre. 

-  Ogni componente finestra può essere spostato tenendo premuto il titolo e trascinando la finestra. 
- Ogni componente finestra può essere bloccato e sbloccato selezionando l'icona della puntina da disegno nella barra del titolo:
    
    ![Blocco degli oggetti](media/ssms-configuration/pushpin.png)

- Ogni componente finestra ha una freccia di elenco a discesa che consente di modificare la finestra in vari modi: 

    ![Opzioni della finestra](media/ssms-configuration/windowoptions.png)

- Quando si hanno due o più finestre di query aperte, è possibile raggrupparle in schede verticali o orizzontali in modo da visualizzarle contemporaneamente. A tale scopo, fare clic con il pulsante destro del mouse sul titolo della query e selezionare l'opzione di scheda desiderata. 
 
    ![Opzioni delle schede query](media/ssms-configuration/querytabbedoptions.png)

    - Questo è il **gruppo di schede orizzontali**: ![Gruppo di schede orizzontali](media/ssms-configuration/horizontaltab.png)     
    
    - Questo è il **gruppo di schede verticali**:  
        ![Gruppo di schede verticali](media/ssms-configuration/verticaltabgroup.png)
        

    - Per riunire le schede, fare nuovamente clic con il pulsante destro del mouse sul titolo della query e selezionare **Move to Next Tab Group** (Passa a gruppo di schede successivo) o **Move to Previous Tab Group** (Passa a gruppo di schede precedente):
    
        ![Unire le schede delle query](media/ssms-configuration/mergetabgroups.png)

- Per ripristinare il layout dell'ambiente predefinito, fare clic sul **menu Finestra** > **Reset Window Layout** (Reimposta layout finestra):
 
    ![Ripristino del layout della finestra](media/ssms-configuration/resetwindowlayout.png)
    
## <a name="maximize-query-editor"></a>Ingrandire l'editor di query
L'editor di query può essere ingrandito alla modalità schermo intero.

1. Fare clic in un punto qualsiasi della finestra dell'editor di query.
2. Premere MAIUSC+ALT+INVIO per passare dalla modalità normale a quella a schermo intero e viceversa. 

Questa scelta rapida da tastiera funziona con tutte le finestre dei documenti. 



## <a name="change-basic-settings"></a>Modificare le impostazioni di base
In questa sezione viene illustrato come modificare alcune impostazioni di base in SSMS. Queste opzioni sono disponibili nell'opzione del menu **Strumenti**:

  ![Menu Strumenti](media/ssms-configuration/tools.png)


- La barra degli strumenti evidenziata può essere modificata passando al menu **Strumenti** > **Personalizza**:

    ![Personalizzare la barra degli strumenti](media/ssms-configuration/toolbar.png)

### <a name="change-the-font"></a>Modificare il tipo di carattere
- Il tipo di carattere può essere modificato dal menu **Strumenti** > **Opzioni** > **Fonts and Colors** (Tipi di carattere e colori):

     ![Tipi di carattere e colori](media/ssms-configuration/fontsandcolors.png)

### <a name="change-the-startup-options"></a>Modificare le opzioni di avvio
- Le opzioni di avvio determinano l'aspetto dell'area di lavoro al primo avvio di SSMS. Possono essere configurate dal menu **Strumenti** > **Opzioni** > **Avvio**:
 
    ![Opzioni di avvio](media/ssms-configuration/startup.png)

### <a name="reset-settings-to-default"></a>Reimpostare i valori predefiniti delle impostazioni
- È possibile esportare e importare tutte queste impostazioni dal menu **Strumenti** > **Import and Export Settings** (Importa/Esporta impostazioni) 

    ![Importare ed esportare impostazioni](media/ssms-configuration/settings.png)
    - Da qui è anche possibile ripristinare tutte le impostazioni predefinite. 


## <a name="next-steps"></a>Passaggi successivi
Nel prossimo articolo verranno presentati alcuni suggerimenti aggiuntivi per l'uso di SSMS, ad esempio la ricerca di log degli errori di SQL Server e del nome dell'istanza SQL. 

Per altre informazioni, vedere l'articolo successivo
> [!div class="nextstepaction"]
> [Pulsante passaggi successivi](ssms-tricks.md)
 
 





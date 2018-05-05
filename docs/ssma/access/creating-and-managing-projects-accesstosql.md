---
title: Creazione e gestione di progetti (AccessToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-access
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- creating projects
- new projects
- opening projects
- projects
- projects, creating and managing
- saving metadata
- saving projects
ms.assetid: f2d1f0b0-5394-4adb-b3f3-abd71eb68ca7
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 4025227271ed2c73d11aef838ef902e2438b2dce
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="creating-and-managing-projects-accesstosql"></a>Creazione e gestione di progetti (AccessToSQL)
Per eseguire la migrazione di database di Access per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, è necessario creare innanzitutto un progetto SSMA. Il progetto è un file che contiene i metadati relativi ai database di Access che si desidera eseguire la migrazione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, i metadati sull'istanza di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure che riceverà la migrazione di oggetti e i dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] informazioni di connessione e le impostazioni del progetto.  
  
## <a name="reviewing-default-project-settings"></a>Verificare le impostazioni di progetto predefinito  
SSMA contiene varie opzioni per la conversione e la sincronizzazione degli oggetti di database e per la conversione dei dati. L'impostazione predefinita per queste opzioni è appropriato per molti utenti. Tuttavia, prima di creare un nuovo progetto SSMA, si deve rivedere le opzioni e, se si desidera, modificare le impostazioni predefinite che verranno utilizzate per tutti i nuovi progetti.  
  
**Per controllare le impostazioni di progetto predefinito**  
  
1.  Nel **strumenti** dal menu **impostazioni di progetto predefinite**.  
  
2.  Selezionare il tipo di progetto in **versione di destinazione della migrazione** elenco a discesa per i quali impostazioni devono essere visualizzati o modificati e quindi fare clic su **generale** scheda.  
  
3.  Nel riquadro a sinistra, fare clic su **conversione**.  
  
4.  Nel riquadro di destra, rivedere le opzioni. Per ulteriori informazioni su queste opzioni, vedere [le impostazioni del progetto (conversione)](http://msdn.microsoft.com/en-us/bcebc635-c638-4ddb-924c-b9ccfef86388).  
  
5.  Modificare le opzioni necessarie.  
  
6.  Ripetere i passaggi precedenti per il **migrazione**, **GUI**, e **del mapping dei tipi** pagine.  
  
    -   Per informazioni sulle opzioni di migrazione, vedere [le impostazioni del progetto (migrazione)](http://msdn.microsoft.com/en-us/4caebc9c-8680-4b99-a8fa-89c43161c95d).  
  
    -   Per informazioni sulle opzioni dell'interfaccia utente, vedere [le impostazioni di progetto (GUI)](http://msdn.microsoft.com/en-us/cf06baf1-8714-48a3-95dc-781f6ca53693).  
  
    -   Per ulteriori informazioni sulle impostazioni di mapping dei tipi di dati, vedere [le impostazioni del progetto (tipo di Mapping)](http://msdn.microsoft.com/en-us/b87b9683-abed-4677-8c50-18bdba704655).  
  
    -   Per informazioni sulle impostazioni di SQL Azure, vedere [le impostazioni del progetto (SQL Azure)](http://msdn.microsoft.com/en-us/bbb8a204-d0e4-4f0b-9709-271feb1f136e).  
  
**Nota** SQL Azure impostazioni saranno disponibili solo quando si seleziona la migrazione a SQL Azure durante la creazione di un progetto.  
  
## <a name="creating-new-projects"></a>Creazione di nuovi progetti  
SSMA viene avviato senza caricare un progetto predefinito. La migrazione dei dati dal database di Access per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, è necessario creare un progetto.  
  
**Per creare un nuovo progetto**  
  
1.  Scegliere **Nuovo progetto** dal menu **File**.  
  
    Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2.  Nel **nome** , immettere un nome per il progetto.  
  
3.  Nel **percorso** immettere o selezionare una cartella per il progetto  
  
4.  Nell'elenco per la migrazione verso il basso, selezionare uno di SQL Server 2005 o SQL Server 2008 / SQL Server 2012 o SQL Server 2014 / 2016 / Azure SQL database di SQL Server, quindi fare clic su **OK**.  
  
SSMA consente di creare il file di progetto. È ora possibile eseguire il passaggio successivo del [aggiunta di uno o più database di Access](http://msdn.microsoft.com/en-us/e944c740-4c8a-4bc1-b0ed-be57bc06dced).  
  
## <a name="customizing-project-settings"></a>Personalizzazione delle impostazioni di progetto  
Inoltre, per definire le impostazioni di progetto predefinite, che si applicano a tutti i nuovi progetti SSMA, è anche possibile personalizzare le impostazioni per ogni progetto. Per ulteriori informazioni, vedere [impostazione conversione e le opzioni di migrazione](http://msdn.microsoft.com/en-us/0a7304df-2f35-4453-96ef-7ac83dea1167).  
  
Quando si personalizza il mapping di tipi di dati tra database di origine e di destinazione, è possibile definire i mapping per il progetto, un database o un livello di oggetto. Per ulteriori informazioni sui mapping dei tipi, vedere [Mapping tipi di origine e destinazione dati](http://msdn.microsoft.com/en-us/b362a075-16e7-423f-b63f-e1e9f02844a9).  
  
## <a name="saving-projects"></a>Il salvataggio dei progetti  
Quando si salva un progetto, SSMA rende permanenti le impostazioni di progetto e, facoltativamente, i metadati del database, al file di progetto.  
  
**Per salvare un progetto**  
  
-   Nel **File** dal menu **Salva progetto**.  
  
    Se i database all'interno del progetto sono state modificate o non sono stati convertiti, SSMA verrà chiesto di salvare i metadati nel progetto. Salvataggio di metadati consente di lavorare offline. È anche possibile inviare un file di progetto completo ad altre persone, tra cui il personale di supporto tecnico. Se viene chiesto di salvare i metadati, eseguire le operazioni seguenti:  
  
    1.  Per ogni database che viene visualizzato lo stato **metadati mancanti**, selezionare la casella di controllo accanto al nome del database.  
  
        Salvataggio di metadati potrebbe richiedere alcuni minuti. Se non si desidera salvare i metadati a questo punto, non selezionare le caselle di controllo.  
  
    2.  Fare clic su **Salva**.  
  
        SSMA analizzerà gli schemi di accesso e salvare i metadati del file di progetto.  
  
## <a name="opening-projects"></a>Apertura di progetti  
Quando si apre un progetto, si viene disconnessi da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Ciò consente di lavorare offline. Per aggiornare gli oggetti di database carica i metadati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Per eseguire la migrazione dei dati, è necessario riconnettersi al [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.  
  
**Per aprire un progetto**  
  
1.  Utilizzare una delle procedure riportate di seguito:  
  
    -   Nel **File** dal menu **progetti recenti**e quindi selezionare il progetto che si desidera aprire.  
  
    -   Nel **File** dal menu **Apri progetto**, individuare il file di progetto .a2ssproj, selezionare il file e quindi fare clic su **aprire**.  
  
2.  Per riconnettersi [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]via il **File** dal menu **Riconnetti a SQL Server**.  
  
3.  Per ristabilire la connessione a SQL Azure, sul **File** dal menu **ristabilire la connessione a SQL Azure.**  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo del processo di migrazione consiste nel [aggiungere uno o più database di Access](http://msdn.microsoft.com/en-us/e944c740-4c8a-4bc1-b0ed-be57bc06dced).  
  
## <a name="see-also"></a>Vedere anche  
[La migrazione dei database di Access a SQL Server](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[Aggiunta e rimozione dei file di Database di Access](http://msdn.microsoft.com/en-us/e944c740-4c8a-4bc1-b0ed-be57bc06dced)  
  

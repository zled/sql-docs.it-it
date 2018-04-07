---
title: Aggiunta e rimozione dell'accesso Database file (AccessToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-access
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Access databases
- adding Access files
- adding and removing Access databases
- browsing Access metadata
- browsing metadata, Access databases
- connecting, Access databases
- databases
- files, adding and removing
- finding Access databases
- finding database files
- locating database files
- metadata
- metadata, browsing
- metadata, refreshing
- refreshing metadata
- removing Access files
- scanning for database files
- searching for database files
ms.assetid: e944c740-4c8a-4bc1-b0ed-be57bc06dced
caps.latest.revision: 15
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9553d01b1fb8c96281fd108d84645d785bd9f028
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="adding-and-removing-access-database-files-accesstosql"></a>Aggiunta e rimozione di file di Database di Access (AccessToSQL)
Per eseguire la migrazione di dati Access [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, è necessario aggiungere uno o più database di Access al progetto SSMA. Questi database devono essere Access 97 o versioni successive. Se sono presenti database da una versione precedente di accesso, è necessario convertire i database in una versione più recente. Farlo aprendo e salvando i database di Access 97 o versione successiva prima di aggiungere SSMA.  
  
## <a name="what-happens-when-you-add-access-database-files"></a>Cosa accade quando si aggiungono file di Database di Access?  
Quando si aggiunge un database di Access a un progetto SSMA, SSMA legge i metadati del database e quindi aggiunge i metadati del file di progetto. Questi metadati viene descritto il database e i relativi oggetti. SSMA utilizza i metadati durante la conversione di oggetti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o sintassi SQL Azure, e quando esegue la migrazione di dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. È possibile esplorare i metadati nel Visualizzatore metadati accesso ed esaminare le proprietà di singoli oggetti di database.  
  
> [!NOTE]  
> Un database di Access può essere diviso in più file: un database back-end che contiene le tabelle e database front-end che contengono le query, form, report, le macro, moduli e tasti di scelta rapida. Se si desidera eseguire la migrazione di un database di divisione per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, aggiungere il database front-end per SSMA.  
  
## <a name="permissions-that-are-required-by-ssma"></a>Autorizzazioni necessarie per SSMA  
Per eseguire la migrazione di un database di Access per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, il gruppo di utenti e l'utente amministratore deve disporre delle autorizzazioni Administer. Per informazioni su come eseguire la migrazione dei database con gruppi di lavoro protezione, vedere [preparare i database di Access per la migrazione](http://msdn.microsoft.com/en-us/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)  
  
## <a name="selecting-databases-to-add"></a>Selezione dei database da aggiungere  
Se si desidera aggiungere uno o più database a un progetto SSMA e i file sono tutti in un percorso noto, è possibile aggiungere i file utilizzando la procedura seguente.  
  
**Per aggiungere singoli file di database**  
  
1.  Nel **File** menu, fare clic su **aggiungere database**.  
  
2.  Nel **aprire** finestra di dialogo, individuare la cartella che contiene i file di database.  
  
3.  Selezionare i file che si desidera aggiungere e quindi fare clic su **aprire**.  
  
## <a name="finding-databases-to-add"></a>Per aggiungere i database di ricerca  
Se si desidera aggiungere più database di Access da cartelle diverse a un progetto SSMA o si desidera aggiungere un singolo file, ma è necessario trovare il file, è possibile seguire questi passaggi per individuare una di più file e li aggiunge al progetto.  
  
**Per trovare e aggiungere database**  
  
1.  Nel **File** menu, fare clic su **trovare database**.  
  
2.  In Creazione guidata database di ricerca, immettere il nome di unità, percorso del file o percorso UNC che si desidera cercare. In alternativa, fare clic su **Sfoglia** per individuare la cartella di rete o unità.  
  
3.  Fare clic su **Aggiungi** aggiungere il percorso all'elenco.  
  
    Ripetere i due passaggi precedenti per aggiungere altri percorsi di ricerca.  
  
4.  Facoltativamente, aggiungere criteri di ricerca per filtrare l'elenco dei database che vengono restituiti.  
  
    > [!IMPORTANT]  
    > Il **tutto o parte del nome file** casella di testo non supporta caratteri jolly.  
  
5.  Fare clic su **analisi**.  
  
    Viene visualizzata la pagina di analisi. Mostra i database che sono stati trovati e lo stato di avanzamento della ricerca. Per interrompere la ricerca, fare clic su **arrestare**.  
  
6.  Nella pagina Seleziona file, selezionare i database che si desidera aggiungere al progetto.  
  
    È possibile utilizzare il **Seleziona tutto** e **Cancella tutto** pulsanti nella parte superiore dell'elenco per selezionare o deselezionare tutti i database. È possibile tenere premuto il tasto CTRL per selezionare più database o tenere premuto il tasto MAIUSC per selezionare un intervallo di database.  
  
7.  Scegliere **Avanti**.  
  
8.  Nella pagina verifica, fare clic su **fine**.  
  
## <a name="browsing-access-metadata"></a>Esplorazione dei metadati di accesso  
Dopo aver aggiunto un database di Access a un progetto, i metadati del progetto viene visualizzato in Visualizzatore metadati di accesso. È possibile esplorare la gerarchia dei database e oggetti di database in Esplora risorse.  
  
**Per esplorare i metadati**  
  
1.  Nel Visualizzatore metadati di accesso, espandere **accesso metabase**, quindi espandere **database**.  
  
2.  Espandere il database che si desidera esaminare e quindi espandere **query**.  
  
    Si noti l'elenco delle query. Se si seleziona una query, un **SQL** scheda e un **proprietà** scheda viene visualizzata nel riquadro di destra.  
  
3.  Espandere **tabelle** e quindi selezionare una tabella.  
  
    Si noti che vengono visualizzati quattro schede: **tabella**, **del mapping dei tipi**, **proprietà**, e **dati**.  
  
4.  Espandere una tabella, **chiavi**, quindi selezionare una chiave.  
  
    Le proprietà chiave vengono visualizzati nel riquadro di destra.  
  
5.  Espandere **indici**, quindi selezionare un indice.  
  
    Le proprietà di indice verranno visualizzate nel riquadro di destra.  
  
## <a name="refreshing-databases"></a>Aggiornamento dei database  
Se un database di Access viene modificato dopo aver aggiunto il file, è possibile aggiornare i metadati dal database di Access.  
  
**Per aggiornare i metadati di accesso**  
  
-   In Visualizzatore metadati di accesso, il database e quindi scegliere **aggiornamento dal Database**.  
  
## <a name="removing-databases"></a>Rimozione di database  
È possibile rimuovere un database di Access da un progetto eseguendo la procedura seguente.  
  
**Per rimuovere un database da un progetto**  
  
1.  Nel Visualizzatore metadati di accesso, espandere **accesso metabase**, quindi espandere **database**.  
  
2.  Il database e quindi scegliere **Rimuovi Database**.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo del processo di migrazione consiste nel [connettersi a SQL Server](http://msdn.microsoft.com/en-us/bb8c4bde-cfc2-4636-92ae-5dd24abe9536).  
  
## <a name="see-also"></a>Vedere anche  
[La migrazione dei database di Access a SQL Server](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[Creazione e gestione di progetti](http://msdn.microsoft.com/en-us/f2d1f0b0-5394-4adb-b3f3-abd71eb68ca7)  
  

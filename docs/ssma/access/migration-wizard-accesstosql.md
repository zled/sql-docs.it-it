---
title: Migrazione guidata (AccessToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Migration Wizard dialog box
- Migration Wizard, adding Access databases
- Migration Wizard, Connect to SQL Azure
- Migration Wizard, Connect to SQL Server
- Migration Wizard, Link Tables
- Migration Wizard, Migration status
- Migration Wizard, New Project
- Migration Wizard, Selecting objects to migrate
ms.assetid: 5bab5914-b2ae-4795-8cf5-83e42d64bef2
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e6b2024b8ba34bd4f71abc6030ae86dcc03faebd
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="migration-wizard-accesstosql"></a>Migrazione guidata (AccessToSQL)
La migrazione guidata in modo semplificato la migrazione di uno o più database dall'accesso al [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Tramite la procedura guidata, verranno creare un progetto, aggiungere il progetto di database, selezionare gli oggetti per eseguire la migrazione e connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. È inoltre convertire, caricare e migrare i dati e schemi di accesso. Facoltativamente, è possibile collegare le tabelle di Access per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tabelle o SQL Azure.  
  
La maggior parte delle pagine della procedura guidata di migrazione contengono le stesse opzioni di finestre di dialogo SSMA esistente. Pertanto, le pagine della procedura guidata sono descritte di seguito, e quindi vengono forniti i collegamenti in modo che altre informazioni sulle singole opzioni. Se una pagina contiene opzioni specifiche, sono documentati di seguito.  
  
## <a name="starting-the-migration-wizard"></a>Avvio della procedura guidata di migrazione  
Per impostazione predefinita, la migrazione guidata viene visualizzata quando si avvia SSMA. È anche possibile avviare la procedura guidata nel **File** menu selezionando **la migrazione guidata**.  
  
## <a name="welcome-page"></a>Pagina introduttiva  
La pagina di benvenuto introduce la migrazione guidata e fornisce l'opzione seguente per avviare la procedura guidata.  
  
**Avviare la procedura guidata all'avvio.**  
Per impostazione predefinita, SSMA avvia la migrazione guidata quando si avvia SSMA. Per impedire l'avvio automatico della procedura guidata, deselezionare questa casella di controllo.  
  
## <a name="create-new-project-page"></a>Creare una nuova pagina del progetto  
La pagina Crea nuovo progetto è possibile immettere il nome e percorso di migrazione progetto tipo di file project (la versione di SQL Server utilizzata per la migrazione di destinazione). Per ulteriori informazioni, vedere [nuovo progetto (SSMA)](http://msdn.microsoft.com/en-us/ca294f6d-eeb5-42ca-9306-156281a3f0f3)  
  
## <a name="add-access-databases-page"></a>Aggiungere una pagina di accesso ai database  
La pagina Aggiungi database di Access è aggiungere uno o più database di Access al progetto. È possibile aggiungere singoli database facendo clic su **aggiungere database**e quindi selezionando i database dal **aprire** finestra. In alternativa, è possibile trovare i database utilizzando il **trovare database** pulsante. Per altre informazioni, vedere gli argomenti seguenti:  
  
-   [Aggiunta e rimozione di file di Database di Access](http://msdn.microsoft.com/en-us/e944c740-4c8a-4bc1-b0ed-be57bc06dced)  
  
-   [Trovare la procedura guidata database (selezione dei percorsi)](http://msdn.microsoft.com/en-us/00b2d32a-998b-47a7-b25c-589b5bd6777a)  
  
-   [Trovare la procedura guidata database (selezionare file)](http://msdn.microsoft.com/en-us/2f574a34-4bab-40a4-89a8-ad4907ffc3fd)  
  
-   [Trovare la procedura guidata database (selezione di verifica)](http://msdn.microsoft.com/en-us/62e20e03-50cc-4ac8-8072-524d194d2ec3)  
  
## <a name="select-objects-to-migrate-page"></a>Selezionare gli oggetti da migrare la pagina  
Per gli oggetti selezionare alla pagina di migrazione, si selezionano oggetti da convertire. È possibile selezionare tutti gli oggetti, gruppi di oggetti o singoli oggetti.  
  
**Per selezionare gli oggetti**  
  
1.  Espandere **accesso metabase**, quindi espandere **database**.  
  
2.  Eseguire una o più delle operazioni seguenti:  
  
    -   Per convertire tutti i database, selezionare la casella di controllo accanto a **database**.  
  
    -   Per convertire o omettere i singoli database, selezionare o deselezionare la casella di controllo accanto al nome del database.  
  
    -   Per convertire o omettere le query, espandere il database, quindi selezionare o deselezionare il **query** casella di controllo.  
  
    -   Per convertire o omettere le singole tabelle, espandere il database, **tabelle**e quindi selezionare o deselezionare la casella di controllo accanto alla tabella.  
  
Se si dispone di molti oggetti, si desidera utilizzare il **Selezione oggetto avanzata** opzioni nel riquadro di destra per filtrare l'accesso degli oggetti di database. Ad esempio, se si seleziona **tabelle** nel riquadro a sinistra, quindi è possibile filtrare l'elenco delle tabelle tramite l'immissione di stringhe nel **filtro** casella. È quindi possibile selezionare o deselezionare le tabelle filtrate per la migrazione utilizzando i pulsanti nella parte superiore del riquadro.  
  
Per ulteriori informazioni sui filtri, vedere la sezione delle opzioni di [selezione di oggetti avanzati (SSMA comune)](http://msdn.microsoft.com/en-us/f53b0c79-5473-410a-a0dc-d8f544f7a63c).  
  
## <a name="connect-to-sql-server-page"></a>Connettersi alla pagina di SQL Server  
Connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] pagina, specificare le proprietà di connessione e quindi connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Per ulteriori informazioni, vedere [Connetti a SQL Server](http://msdn.microsoft.com/en-us/00e0432e-ec26-4ab4-af64-c9ca760e3541)  
  
> [!IMPORTANT]  
> Non appena la connessione ha esito positivo, si verificheranno **Collega tabelle** pagina in cui è presente un'opzione di collegamento tra le tabelle. Fare clic su **Avanti** e avvia la migrazione.  
  
## <a name="connect-to-sql-azure-page"></a>Connettersi a SQL Azure pagina  
Nella pagina Connetti a SQL Azure, specificare le proprietà di connessione e quindi connettersi a SQL Azure. Per creare un nuovo database di azure, è possibile farlo tramite **Create Database Azure** opzione visualizzata fare clic su di **Sfoglia** pulsante. Per ulteriori informazioni, vedere [Connetti a SQL Azure](http://msdn.microsoft.com/en-us/bf44b236-d9be-41ae-a5fd-bd73038e505f)  
  
> [!IMPORTANT]  
> Non appena la connessione ha esito positivo, si verificheranno **Collega tabelle** pagina in cui è presente un'opzione di collegamento tra le tabelle. Fare clic su **Avanti** pulsante pagina di collegamenti per avviare la migrazione.  
  
## <a name="link-tables-page"></a>Pagina di tabelle di collegamento  
La pagina di tabelle di collegamento consente di collegare le tabelle di Access originale dopo la migrazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o tabelle di SQL Azure. Collegamento delle tabelle di modifica nel database di Access in modo che i dati di utilizzare pagine di accesso ai dati, moduli, report e query di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database di SQL Azure anziché i dati nel database di Access.  
  
**Tabelle di collegamento**  
Selezionare il **collegare tabelle** casella di controllo per accedere a tabelle di collegamento per la migrazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o tabelle di SQL Azure. Per avviare la migrazione è necessario fare clic **Avanti** pulsante.  
  
## <a name="migration-status-page"></a>Pagina relativa allo stato di migrazione  
Nella pagina di migrazione stato viene visualizzato lo stato di conversione gli schemi di accesso da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o schemi di SQL Azure, il caricamento degli schemi convertiti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, e quindi la migrazione dei dati.  
  
Per ulteriori informazioni su questa pagina, vedere [Converti, carica ed eseguire la migrazione](http://msdn.microsoft.com/en-us/4ec83e96-88a5-4b7b-8d5a-f3429d9a936b)  
  
## <a name="see-also"></a>Vedere anche  
[Introduzione a SQL Server Migration Assistant per Access &#40; AccessToSQL &#41;](../../ssma/access/getting-started-with-sql-server-migration-assistant-for-access-accesstosql.md)  
[Migrazione di database di Access a SQL Server](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[Reference(Access) dell'interfaccia utente](http://msdn.microsoft.com/en-us/af24c303-4a41-449b-9c86-d6558a97e839)  
  


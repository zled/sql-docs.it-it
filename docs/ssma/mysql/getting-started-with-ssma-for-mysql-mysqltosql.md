---
title: Introduzione a SSMA per MySQL (MySQLToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
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
- Getting started, MySQL metadata explorer
- Getting started, SQL Server or SQL Azure metadata explorer
- Getting started,Installing and licensing
ms.assetid: 8ebfa061-be6f-4a07-923f-8dc832a82f70
caps.latest.revision: 19
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: efe3b32103e655213cecedbc9312233d5fd2c2d9
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="getting-started-with-ssma-for-mysql-mysqltosql"></a>Introduzione a SSMA per MySQL (MySQLToSQL)
SQL Server Migration Assistant (SSMA) per MySQL consente di convertire gli schemi di database MySQL in schemi di SQL Server o database SQL di Azure, caricare gli schemi risultanti in SQL Server o database SQL di Azure e la migrazione dei dati da MySQL a SQL Server o database SQL di Azure.  
  
In questo argomento introduce il processo di installazione e quindi consente di acquisire familiarità con l'interfaccia utente SSMA.  
  
## <a name="installing-ssma"></a>L'installazione di SSMA  
Per utilizzare SSMA, è necessario installare il programma client SSMA in un computer che può accedere al database MySQL di origine sia l'istanza di destinazione di SQL Server o database SQL di Azure. Quindi, installare i provider di MySQL (MySQL 5.1 provider ODBC (attendibile)) nel computer in cui è in esecuzione il programma di Client SSMA. Per istruzioni sull'installazione, vedere [installazione di SSMA per MySQL &#40;MySqlToSql&#41;](../../ssma/mysql/installing-ssma-for-mysql-mysqltosql.md)  
  
Per avviare SSMA, fare clic su **avviare**, scegliere **tutti i programmi**, scegliere **SQL Server Migration Assistant per MySQL**, quindi fare clic su **SQL Server Migration Assistant per MySQL**.  
  
## <a name="ssma-for-mysql-user-interface"></a>SSMA per l'interfaccia utente di MySQL  
Dopo aver installato e concesso in licenza SSMA, è possibile utilizzare SSMA per eseguire la migrazione di database MySQL a SQL Server o database SQL di Azure. È utile per acquisire familiarità con l'interfaccia utente SSMA prima di iniziare. Il diagramma seguente mostra l'interfaccia utente per SSMA, incluse le finestre di esplorazione dei metadati, metadati, le barre degli strumenti, riquadro di output e riquadro elenco errori:  
  
![SSMA per l'interfaccia utente grafica di MySql](../../ssma/mysql/media/ssmaformysqlgui.gif "SSMA per l'interfaccia utente grafica di MySql")  
  
Per avviare una migrazione, è necessario:  
  
1.  Creare un nuovo progetto.  
  
2.  Connettersi a un database MySQL.  
  
3.  Dopo la connessione ha esito positivo, gli schemi di MySQL verranno visualizzato in Visualizzatore metadati MySQL. Oggetti pulsante destro del mouse in Visualizzatore metadati MySQL per eseguire attività quali la creano di report che valutano le conversioni in database SQL di SQL Server/Azure.  
  
È anche possibile eseguire queste attività tramite i menu e barre degli strumenti.  
  
Inoltre, è necessario connettersi a un'istanza di SQL Server. Dopo la connessione ha esito positivo, verrà visualizzata una gerarchia di database di SQL Server in Esplora i metadati di SQL Server. Dopo la conversione degli schemi di MySQL in schemi di SQL Server, selezionare gli schemi convertiti in Visualizzatore metadati di SQL Server e quindi sincronizzare gli schemi con SQL Server.  
  
Se è stato selezionato un database SQL di Azure dalla migrazione per l'elenco a discesa nella finestra di dialogo Nuovo progetto, è necessario connettersi al database SQL di Azure. Dopo la connessione ha esito positivo, una gerarchia di database di SQL Azure database verrà visualizzato in Visualizzatore metadati di database SQL Azure. Dopo la conversione degli schemi di MySQL in schemi di database SQL di Azure, selezionare gli schemi convertiti in Visualizzatore metadati di database SQL Azure e quindi sincronizzare gli schemi con database SQL di Azure.  
  
Dopo aver sincronizzato gli schemi convertiti con SQL Server o database SQL di Azure, è possibile tornare a Visualizzatore metadati MySQL e la migrazione dei dati da schemi di MySQL in database di SQL Server o database SQL di Azure.  
  
Per ulteriori informazioni su queste attività e su come eseguirle, vedere [la migrazione di database MySQL a SQL Server - database SQL di Azure &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md).  
  
Nelle sezioni seguenti vengono descritte le funzionalità dell'interfaccia utente SSMA.  
  
### <a name="metadata-explorers"></a>Finestre di esplorazione dei metadati  
SSMA contiene due finestre di esplorazione dei metadati per individuare ed eseguire azioni sul database MySQL e SQL Server.  
  
### <a name="mysql-metadata-explorer"></a>Visualizzatore metadati MySQL  
Visualizzatore metadati MySQL Mostra informazioni sugli schemi di MySQL. Tramite Visualizzatore metadati MySQL, è possibile eseguire le attività seguenti:  
  
-   Esplorare gli oggetti in ogni schema.  
  
-   Selezionare gli oggetti per la conversione e quindi convertire gli oggetti per la sintassi SQL Server. Per altre informazioni, vedere [conversione database MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
-   Selezionare le tabelle per la migrazione dei dati e quindi migrare i dati da tali tabelle a SQL Server. Per altre informazioni, vedere [la migrazione dei dati di MySQL in SQL Server - database SQL di Azure &#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
### <a name="sql-server-or-azure-sql-db-metadata-explorer"></a>SQL Server o Visualizzatore metadati di database SQL di Azure  
SQL Server o Visualizzatore metadati di database SQL Azure Mostra informazioni su un'istanza di SQL Server o database SQL di Azure. Quando ci si connette a un'istanza di SQL Server o database SQL di Azure, SSMA recupera i metadati relativi a tale istanza e lo archivia nel file di progetto.  
  
È possibile utilizzare questo Visualizzatore metadati per convertire gli oggetti di database MySQL selezionare e quindi sincronizzare gli oggetti con l'istanza di SQL Server o database SQL di Azure.  
  
Per altre informazioni, vedere [sincronizzazione (MySQL a SQL Server / database SQL di Azure)](http://msdn.microsoft.com/en-us/ac993a6d-0283-4823-8793-6b217677dfa3)  
  
### <a name="metadata"></a>Metadati  
A destra di ogni Visualizzatore metadati sono schede che descrivono l'oggetto selezionato. Ad esempio, se si seleziona una tabella in Visualizzatore metadati MySQL, verranno visualizzate nove schede: **tabella**, **SQL**, **del mapping dei tipi**, **dati**, **impostazioni**, **Charset Mapping**, **modalità SQL**, **proprietà**, e **Report**. Il **Report** scheda contiene informazioni solo dopo aver creato un report che contiene l'oggetto selezionato. Se si seleziona una tabella in Visualizzatore metadati di SQL Server, verranno visualizzate tre schede: **tabella**, **SQL** e **dati**.  
  
La maggior parte delle impostazioni dei metadati sono di sola lettura. Tuttavia, è possibile modificare i metadati seguenti:  
  
-   In Visualizzatore metadati MySQL, è possibile modificare i mapping dei tipi, Mapping di set di caratteri, la modalità di SQL. Per convertire il mapping dei tipi modificata o il Mapping di set di caratteri o modalità SQL, è possibile apportare modifiche prima di convertire gli schemi.  
  
-   In Esplora i metadati di SQL Server, è possibile modificare le proprietà di tabella e indice nella scheda della tabella. Per visualizzare le modifiche in SQL Server, è possibile apportare queste modifiche prima di caricare gli schemi in SQL Server.  
  
Le modifiche apportate in un Visualizzatore metadati vengono riflesse nei metadati del progetto, non nei database di origine o di destinazione.  
  
### <a name="toolbars"></a>Barre degli strumenti  
SSMA è due barre degli strumenti: una barra degli strumenti del progetto e una barra degli strumenti di migrazione.  
  
### <a name="the-project-toolbar"></a>La barra degli strumenti del progetto  
La barra degli strumenti del progetto contiene pulsanti per l'utilizzo di progetti, la connessione a MySQL e connessione a SQL Server o database SQL di Azure. Questi pulsanti sono simili a quelli nel **File** menu.  
  
### <a name="migration-toolbar"></a>Barra degli strumenti di migrazione  
La tabella seguente illustra la migrazione di comandi della barra degli strumenti:  
  
|||  
|-|-|  
|**Button**|**Funzione**|  
|**Creazione di Report**|Converte gli oggetti selezionati di MySQL in oggetti di SQL Server o database SQL di Azure e quindi crea un report che mostra come esito positivo della conversione.<br /><br />Questo comando è disabilitato a meno che non vengono selezionati gli oggetti in Visualizzatore metadati MySQL.|  
|**Converti Schema**|Converte gli oggetti selezionati di MySQL in oggetti di SQL Server o database SQL di Azure.<br /><br />Questo comando è disabilitato a meno che non vengono selezionati gli oggetti in Visualizzatore metadati MySQL.|  
|**La migrazione dei dati**|Esegue la migrazione di dati dal database di MySQL a SQL Server o database SQL di Azure. Prima di eseguire questo comando, è necessario convertire gli schemi di MySQL in schemi di SQL Server o database SQL di Azure e quindi caricare gli oggetti in SQL Server o database SQL di Azure.<br /><br />Questo comando è disabilitato a meno che non vengono selezionati gli oggetti in Visualizzatore metadati MySQL.|  
|**Arresta**|Arresta il processo corrente.|  
  
### <a name="menus"></a>Menu  
Nella tabella seguente viene illustrato i menu SSMA.  
  
|||  
|-|-|  
|**Menu**|**Description**|  
|**File**|Contiene i comandi per l'utilizzo di progetti, la connessione a MySQL e connessione a SQL Server o database SQL di Azure.|  
|**Modifica**|Contiene i comandi per la ricerca e l'utilizzo del testo nelle pagine di dettagli. Per aprire **gestire segnalibri** finestra di dialogo, dal menu Modifica, fare clic su Gestisci segnalibri. Nella finestra di dialogo verrà visualizzato un elenco di segnalibri. È possibile utilizzare i pulsanti sul lato destro della finestra di dialogo per gestire i segnalibri.|  
|**Visualizza**|Contiene il **sincronizzare i metadati Explorers** comando. Che consente di sincronizzare gli oggetti tra Visualizzatore metadati MySQL e SQL Server o Visualizzatore metadati di database SQL Azure. Contiene inoltre i comandi per visualizzare e nascondere il **Output** e **elenco errori** riquadri e un'opzione **layout** da gestire con il layout.|  
|**Strumenti**|Comandi per creare report, convertire schema, di aggiornamento dal database, eseguire la migrazione di oggetti e dati e salvare come Script. È inoltre possibile accedere al **impostazioni globali, le impostazioni di progetto predefinito** e **impostazioni progetto** finestre di dialogo.|  
|**?**|Fornisce l'accesso di SSMA Guida in linea e di ottenere il **su** la finestra di dialogo.|  
  
### <a name="output-pane-and-error-list-pane"></a>Riquadro di output e il riquadro elenco errori  
Il **vista** menu sono disponibili comandi per attivare o disattivare la visibilità del riquadro di Output e il riquadro elenco errori:  
  
-   Il riquadro di Output Mostra i messaggi di stato da SSMA durante la conversione degli oggetti di sincronizzazione dell'oggetto e migrazione dei dati.  
  
-   Nel riquadro elenco errori Mostra messaggi di errore, avviso e informativi in un elenco ordinabile.  
  
## <a name="see-also"></a>Vedere anche  
[Riferimento all'interfaccia utente &#40;MySQLToSQL&#41;](../../ssma/mysql/user-interface-reference-mysqltosql.md)  
[La migrazione dei dati di MySQL in SQL Server - database SQL di Azure &#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  

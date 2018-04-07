---
title: Database (SQL Server PDW) tempdb
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5840033d-2dc6-4576-8a5f-067e2a58b170
caps.latest.revision: 22
ms.workload: not set
ms.openlocfilehash: 6a52f21b266d277f3bda205803d38431598545f7
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="tempdb-database"></a>Database tempdb
**tempdb** è un database di sistema di SQL Server PDW che archivia le tabelle temporanee locali per i database utente. Tabelle temporanee vengono spesso utilizzate per migliorare le prestazioni delle query. Ad esempio, utilizzare una tabella temporanea per modularizzare uno script e il riutilizzo dei dati calcolati.  
  
Per ulteriori informazioni sui database di sistema, vedere [database di sistema](system-databases.md).  
  
## <a name="Basics"></a>Termini e concetti chiave  
*tabella temporanea locale*  
Oggetto *tabella temporanea locale* utilizza il prefisso # prima il nome della tabella e una tabella temporanea creata da una sessione utente locale. In ogni sessione è possibile accedere solo i dati in tabelle temporanee locali per la propria sessione.  
  
Ogni sessione è possibile visualizzare i metadati per le tabelle temporanee locali in tutte le sessioni. Ad esempio, tutte le sessioni possono visualizzare i metadati per tutte le tabelle temporanee locali con la `SELECT * FROM tempdb.sys.tables` query.  
  
tabella temporanea globale  
*Le tabelle temporanee globali*, supportata in SQL Server con il # # sintassi, non sono supportati in questa versione di SQL Server PDW.  
  
pdwtempdb  
**pdwtempdb** è il database che archivia le tabelle temporanee locali.  
  
PDW non implementa le tabelle temporanee tramite SQL Server**tempdb** database. In alternativa, PDW li archivia in un database denominato pdwtempdb. Questo database è presente in ogni nodo di calcolo e invisibile all'utente tramite le interfacce PDW. Nella Console di amministrazione, nella pagina di archiviazione, si vedranno questi corrispondono per in un database di sistema PDW denominato **tempdb sql**.  
  
tempdb  
**tempdb** è il database tempdb di SQL Server. Usa la registrazione minima. SQL Server Usa tempdb nei nodi di calcolo per archiviare le tabelle temporanee necessarie durante l'esecuzione di operazioni di SQL Server.  
  
SQL Server PDW Elimina tabelle da **tempdb** quando:  
  
-   Viene eseguita l'istruzione DROP TABLE.  
  
-   Una sessione viene disconnessa. Vengono eliminate solo le tabelle temporanee per la sessione.  
  
-   Il dispositivo viene arrestato.  
  
-   Il nodo di controllo dispone di un cluster di failover.  
  
## <a name="general-remarks"></a>Osservazioni generali  
SQL Server PDW esegue le stesse operazioni in tabelle temporanee e tabelle permanenti se non specificato diversamente in modo esplicito. Ad esempio, i dati in tabelle temporanee locali, analogamente alle tabelle permanenti, distribuiti o replicati in tutti i nodi di calcolo.  
  
## <a name="LimitationsRestrictions"></a>Limitazioni e restrizioni  
Limitazioni e restrizioni in SQL Server PDW**tempdb** database. Si *non è possibile:*  
  
-   Creare una tabella temporanea globale che inizia con # #.  
  
-   Eseguire un backup o ripristino di **tempdb**.  
  
-   Modificare le autorizzazioni per **tempdb** con il **GRANT**, **DENY**, o **revocare** istruzioni.  
  
-   Eseguire **DBCC SHRINKLOG** per **tempdb**tempdb.  
  
-   Eseguire le operazioni DDL **tempdb**. Esistono due eccezioni a questa. Per informazioni dettagliate, vedere l'elenco seguente di limitazioni e restrizioni in tabelle temporanee locali.  
  
Limitazioni e restrizioni per le tabelle temporanee locali. Si *non è possibile:*  
  
-   Rinominare una tabella temporanea  
  
-   Creare indici non cluster, viste o le partizioni in una tabella temporanea. **ALTER INDEX** può essere usato per ricompilare un indice cluster per una tabella creato con uno.  
  
-   Modificare le autorizzazioni per le tabelle temporanee con l'istruzione GRANT, DENY o revocare le istruzioni.  
  
-   Eseguire i comandi della console database nelle tabelle temporanee.  
  
-   Utilizzare lo stesso nome per due o più tabelle temporanee all'interno dello stesso batch. Se si usa più di una tabella temporanea locale all'interno di un batch, ogni tabella deve avere un nome univoco. Se più sessioni eseguono lo stesso batch e crea la tabella temporanea locale stesso, SQL Server PDW aggiunge internamente un suffisso numerico al nome della tabella temporanea locale per gestire un nome univoco per ogni tabella temporanea locale.  
  
> [!NOTE]  
> Si *possibile* creare e aggiornare le statistiche in una tabella temporanea. **ALTER INDEX** può essere utilizzato per ricompilare un indice cluster.  
  
## <a name="permissions"></a>Autorizzazioni  
Qualsiasi utente può creare oggetti temporanei in tempdb. Gli utenti possono accedere solo ai propri oggetti, a meno che non ottengano ulteriori autorizzazioni. È possibile revocare l'autorizzazione per la connessione a tempdb per impedire a un utente di utilizzarlo, tuttavia questa operazione non è consigliabile poiché in alcune operazioni di routine è richiesto l'utilizzo di tempdb.  
  
## <a name="RelatedTasks"></a>Attività correlate  
  
|Attività|Description|  
|---------|---------------|  
|Creare una tabella in **tempdb**.|È possibile creare una tabella temporanea di utente con le istruzioni CREATE TABLE e CREATE TABLE AS SELECT. Per ulteriori informazioni, vedere [CREATE TABLE](../t-sql/statements/create-table-azure-sql-data-warehouse.md) e [CREATE TABLE AS SELECT](../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md).|  
|Visualizzare un elenco delle tabelle esistenti in **tempdb**.|`SELECT * FROM tempdb.sys.tables;`|  
|Visualizzare un elenco di colonne esistenti nella **tempdb**.|`SELECT * FROM tempdb.sys.columns;`|  
|Visualizzare un elenco di oggetti esistenti in **tempdb**.|`SELECT * FROM tempdb.sys.objects;`|  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  

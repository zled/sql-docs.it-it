---
title: Supporto per colonne di tipo sparse in SQL Server Native Client | Documenti Microsoft
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client|features
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sparse columns, ODBC
- sparse columns, SQL Server Native Client
- sparse columns, OLE DB
ms.assetid: aee5ed81-7e23-42e4-92d3-2da7844d9bc3
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7f4d77722108f82733978b5b2c778ddfbfb958c9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sparse-columns-support-in-sql-server-native-client"></a>Supporto per colonne di tipo sparse in SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supporta le colonne di tipo sparse. Per ulteriori informazioni sulle colonne di tipo sparse [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vedere [utilizzare le colonne di tipo Sparse](../../../relational-databases/tables/use-sparse-columns.md) e [usare set di colonne](../../../relational-databases/tables/use-column-sets.md).  
  
 Per ulteriori informazioni sulle colonne di tipo sparse supporto in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, vedere [supporta colonne di tipo Sparse &#40;ODBC&#41; ](../../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md) e [supporta colonne di tipo Sparse &#40;OLE DB&#41; ](../../../relational-databases/native-client/ole-db/sparse-columns-support-ole-db.md) .  
  
 Per informazioni sulle applicazioni di esempio che illustrano questa funzionalità, vedere [esempi di programmazione dati di SQL Server](http://msftdpprodsamples.codeplex.com/).  
  
## <a name="user-scenarios-for-sparse-columns-and-sql-server-native-client"></a>Scenari utente per colonne di tipo sparse e SQL Server Native Client  
 Nella tabella seguente vengono descritti in breve gli scenari comuni per gli utenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client che utilizzano colonne di tipo sparse:  
  
|Scenario|Comportamento|  
|--------------|--------------|  
|**Selezionare \* dalla tabella** o IOpenRowset:: OPENROWSET.|Restituisce tutte le colonne che non sono membri di tipo sparse **column_set**, nonché una colonna XML che contiene i valori di tutte le colonne non null che sono membri di tipo sparse **column_set**.|  
|Fare riferimento a una colonna in base al nome.|La colonna è possibile fare riferimento indipendentemente dal relativo stato della colonna di tipo sparse o **column_set** appartenenza.|  
|Accesso **column_set** colonne membro tramite una colonna XML calcolata.|Colonne che sono membri di tipo sparse **column_set** accessibili selezionando il **column_set** in base al nome e possono avere valori inseriti e aggiornati aggiornando il codice XML di **column_set** colonna.<br /><br /> Il valore deve essere conforme allo schema per **column_set** colonne.|  
|Recuperare i metadati per tutte le colonne in una tabella tramite SQLColumns con un criterio di ricerca colonna pari a '% s' (ODBC) o NULL o tramite il set di righe dello schema DBSCHEMA_COLUMNS senza restrizioni di colonna (OLE DB).|Restituisce una riga per tutte le colonne che non sono membri di un **column_set**. Se la tabella è di tipo sparse **column_set**, verrà restituita una riga per tale.<br /><br /> Si noti che questo comportamento non restituisce i metadati per le colonne che sono membri di un **column_set**.|  
|Recuperare i metadati per tutte le colonne, indipendentemente dal tipo sparse o l'appartenenza a un **column_set**. È possibile che venga restituito un numero molto elevato di righe.|Impostare il campo di descrizione SQL_SOPT_SS_NAME_SCOPE su SQL_SS_NAME_SCOPE_EXTENDED e chiamare [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md) (ODBC).<br /><br /> Chiamare IDBSchemaRowset:: GetRowset per il set di righe dello schema DBSCHEMA_COLUMNS_EXTENDED (OLE DB).<br /><br /> Questo scenario non è possibile da un'applicazione che utilizza [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client da una versione precedente a [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Tale applicazione, tuttavia, può eseguire direttamente query viste di sistema.|  
|Recuperare metadati solo per le colonne che sono membri di un **column_set**. È possibile che venga restituito un numero molto elevato di righe.|Impostare il campo di descrizione SQL_SOPT_SS_NAME_SCOPE su SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET e chiamare SQLColumns (ODBC).<br /><br /> Chiamare IDBSchemaRowset:: GetRowset per il set di righe dello schema DBSCHEMA_SPARSE_COLUMN_SET (OLE DB).<br /><br /> Questo scenario non è possibile da un'applicazione che utilizza [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client da una versione precedente a [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Tale applicazione, tuttavia, può eseguire query sulle viste di sistema.|  
|Determinare se una colonna è di tipo sparse.|Esaminare la colonna SS_IS_SPARSE del set di risultati SQLColumns (ODBC).<br /><br /> Esaminare la colonna SS_IS_SPARSE del set di righe dello schema DBSCHEMA_COLUMNS (OLE DB).<br /><br /> Questo scenario non è possibile da un'applicazione che utilizza [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client da una versione precedente a [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Tale applicazione, tuttavia, può eseguire query sulle viste di sistema.|  
|Determinare se una colonna è un **column_set**.|Esaminare la colonna SS_IS_COLUMN_SET del set di risultati SQLColumns. In alternativa, esaminare l'attributo di colonna specifico di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SQL_CA_SS_IS_COLUMN_SET (ODBC).<br /><br /> Esaminare la colonna SS_IS_COLUMN_SET del set di righe dello schema DBSCHEMA_COLUMNS. Oppure consultare *dwFlags* restituito da IColumnsInfo:: GetColumnInfo o DBCOLUMNFLAGS nel set di righe restituito da IColumnsRowset::. Per **column_set** colonne, DBCOLUMNFLAGS_SS_ISCOLUMNSET sarà impostato (OLE DB).<br /><br /> Questo scenario non è possibile da un'applicazione che utilizza [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client da una versione precedente a [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Tale applicazione, tuttavia, può eseguire query sulle viste di sistema.|  
|Importazione ed esportazione di colonne di tipo sparse tramite BCP per una tabella senza **column_set**.|Nessuna modifica nel comportamento rispetto alle versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|Importazione ed esportazione di colonne di tipo sparse tramite BCP per una tabella con un **column_set**.|Il **column_set** è importati ed esportati nello stesso modo in XML, ovvero come **varbinary (max)** se associato come tipo binario oppure come **nvarchar (max)** se associato come un **char** o **wchar** tipo.<br /><br /> Colonne che sono membri di tipo sparse **column_set** non vengono esportate come colonne distinte, ma vengono esportate solo nel valore della **column_set**.|  
|**QUERYOUT** comportamento per BCP.|Nessuna modifica nella gestione di colonne denominate in modo esplicito rispetto alle versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.<br /><br /> Gli scenari che comportano l'importazione e l'esportazione tra tabelle con schemi diversi possono richiedere una gestione speciale.<br /><br /> Per ulteriori informazioni su BCP, vedere Supporto per la copia bulk (BCP) per colonne di tipo sparse più avanti in questo argomento.|  
  
## <a name="down-level-client-behavior"></a>Comportamento dei client legacy  
 I client legacy restituiscono metadati solo per le colonne che non sono membri di tipo sparse **column_set** per SQLColumns e DBSCHMA_COLUMNS. I set di righe dello schema OLE DB aggiuntivi introdotti in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client non sarà disponibile né saranno le modifiche apportate a SQLColumns di ODBC tramite SQL_SOPT_SS_NAME_SCOPE.  
  
 I client legacy possono accedere le colonne che sono membri di tipo sparse **column_set** in base al nome e **column_set** colonna sarà accessibile come colonna XML per [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] client.  
  
## <a name="bulk-copy-bcp-support-for-sparse-columns"></a>Supporto per la copia bulk (BCP) per colonne di tipo sparse  
 Sono state apportate modifiche all'API BCP in ODBC o OLE DB per le colonne di tipo sparse o **column_set** funzionalità.  
  
 Se una tabella include un **column_set**, colonne di tipo sparse non vengono gestite come colonne distinte. I valori di tutte le colonne di tipo sparse sono inclusi nel valore della **column_set**, che viene esportato come una colonna XML; vale a dire come **varbinary (max)** se associato come tipo binario oppure come  **nvarchar (max)** se associato come un **char** o **wchar** tipo). Durante l'importazione, il **column_set** valore deve essere conforme allo schema del **column_set**.  
  
 Per **queryout** operazioni, sussiste alcuna modifica al modo in cui viene fatto riferimento in modo esplicito le colonne vengono gestite. **COLUMN_SET** colonne hanno lo stesso comportamento delle colonne XML e il tipo sparse non ha alcun effetto sulla gestione di colonne di tipo sparse denominate.  
  
 Tuttavia, se **queryout** viene utilizzato per l'esportazione e si fa riferimento le colonne di tipo sparse che sono membri di una colonna di tipo sparse impostata in base al nome, non è possibile eseguire un'importazione diretta in una tabella dalla struttura analoga. In questo modo l'utilità BCP utilizza metadati consistenti con un **selezionare \***  operazione per l'importazione ed è Impossibile trovare la corrispondenza **column_set** colonne membri con questi metadati. Per importare **column_set** colonne membri singolarmente, è necessario definire una visualizzazione sulla tabella che fa riferimento l'oggetto desiderato **column_set** colonne ed è necessario eseguire l'operazione di importazione utilizzando la visualizzazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione in SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  

---
title: Proprietà (OLE DB) dell'origine dati | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- OLE DB data source properties [SQL Server Native Client]
ms.assetid: 6e14fefc-4e0b-4847-a833-4cf0abe65d50
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f108559bebad1ab98fc0c81ce0492293a9632e5b
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37419326"
---
# <a name="data-source-properties-ole-db"></a>Proprietà delle origini dati (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client implementa proprietà origine dati come indicato di seguito.  
  
|ID proprietà|Description|  
|-----------------|-----------------|  
|DBPROP_CURRENTCATALOG|L/S: Lettura/scrittura Impostazione predefinita: Nessuna<br /><br /> Descrizione: Il valore di DBPROP_CURRENTCATALOG indica il database corrente per un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sessione del provider OLE DB Native Client. Impostando il valore della proprietà ha l'effetto identico impostando il database corrente usando il [!INCLUDE[tsql](../../includes/tsql-md.md)] utilizzo *database* istruzione.<br /><br /> A partire [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], se si chiama [sp_defaultdb](../../relational-databases/system-stored-procedures/sp-defaultdb-transact-sql.md) e specificare il nome del database in caratteri minuscoli, anche se il database è stato creato con un nome di case misto, DBPROP_CURRENTCATALOG restituirà il nome in lettere minuscole. Con le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], DBPROP_CURRENTCATALOG restituisce invece la combinazione di maiuscole e minuscole prevista.|  
|DBPROP_MULTIPLECONNECTIONS|L/S: Lettura/scrittura Impostazione predefinita: VARIANT_FALSE<br /><br /> Descrizione: Se la connessione esegue un comando che non produce un set di righe o produce un set di righe che non è un cursore server e si esegue un altro comando, verrà creata una nuova connessione per eseguire il nuovo comando se DBPROP_MULTIPLECONNECTIONS è VARIANT_TRUE.<br /><br /> Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non creerà un'altra connessione se DBPROP_MULTIPLECONNECTION è VARIANT_FALSE o se una transazione è attiva nella connessione. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce DB_E_OBJECTOPEN se DBPROP_MULTIPLECONNECTIONS è VARIANT_FALSE e restituisce E_FAIL se è presente una transazione attiva. Le transazioni e il blocco vengono gestiti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per singola connessione. Se viene generata una seconda connessione, i comandi sulle connessioni separate non condividono blocchi. Per assicurarsi che un comando non blocchi un altro comando, mantenere attivi i blocchi sulle righe richieste da quest'ultimo. Ciò vale anche nel caso di creazione di più sessioni.<br /><br /> Ogni sessione ha una connessione separata.|  
  
 Nel provider specifici set di proprietà DBPROPSET_SQLSERVERDATASOURCE il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client definisce le proprietà dell'origine dati aggiuntivi seguenti.  
  
|ID proprietà|Description|  
|-----------------|-----------------|  
|SSPROP_ENABLEFASTLOAD|L/S: Lettura/scrittura Impostazione predefinita: VARIANT_FALSE<br /><br /> Descrizione: Per abilitare la copia bulk dalla memoria, la proprietà SSPROP_ENABLEFASTLOAD deve essere impostata su VARIANT_TRUE. Con questa proprietà è impostata sull'origine dati, la sessione appena creata consente l'accesso di consumer per il [IRowsetFastLoad](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md) interfaccia.<br /><br /> Se la proprietà è impostata su VARIANT_TRUE, **IRowsetFastLoad** interfaccia è disponibile attraverso **IOpenRowset:: OPENROWSET** richiedendo il **IID_IRowsetFastLoad** interfaccia oppure impostando **SSPROP_IRowsetFastLoad** su VARIANT_TRUE.|  
|SSPROP_ENABLEBULKCOPY|L/S: Lettura/scrittura Impostazione predefinita: VARIANT_FALSE<br /><br /> Descrizione: Per abilitare la copia bulk dai file, la proprietà SSPROP_ENABLEBULKCOPY deve essere impostata su VARIANT_TRUE. Se questa proprietà è impostata sull'origine dati, l'accesso del consumer all'interfaccia IBCPSession è disponibile allo stesso livello delle sessioni.<br /><br /> Anche SSPROP_IRowsetFastLoad deve essere impostato su VARIANT_TRUE.|  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti origine dati &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  

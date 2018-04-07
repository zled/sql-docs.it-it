---
title: Parametri di comando | Documenti Microsoft
description: Parametri di comando
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-commands
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- parameters [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, parameters
- OLE DB Driver for SQL Server, commands
- parameters [OLE DB Driver for SQL Server], OLE DB
- commands [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a9358369e5c6c5c57bc6000689f831a405d16e5d
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="command-parameters"></a>Parametri dei comandi
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  I parametri sono contrassegnati nel testo dei comandi dal carattere del punto interrogativo. L'istruzione SQL seguente è ad esempio contrassegnata per un solo parametro di input:  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 Per migliorare le prestazioni riducendo il traffico di rete, il Driver OLE DB per SQL Server non deduce automaticamente le informazioni sui parametri, a meno che **ICommandWithParameters:: GetParameterInfo** o **ICommandPrepare:: Preparare** viene chiamato prima di eseguire un comando. Ciò significa che il Driver OLE DB per SQL Server non automaticamente:  
  
-   Verificare la correttezza del tipo di dati specificato con **ICommandWithParameters:: SetParameterInfo**.  
  
-   Eseguire il mapping tra il valore DBTYPE specificato nelle informazioni relative all'associazione della funzione di accesso e il tipo di dati di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] corretto per il parametro.  
  
 Se si specificano tipi di dati non compatibili con il tipo di dati di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] del parametro, è possibile che vengano ricevuti errori o che si verifichi una perdita della precisione con entrambi i metodi.  
  
 Per evitare che ciò si verifichi, è necessario:  
  
-   Verificare che *pwszDataSourceType* corrisponde la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] del tipo di dati per il parametro se hardcoded **ICommandWithParameters:: SetParameterInfo**.  
  
-   Assicurarsi che il valore DBTYPE associato al parametro sia dello stesso tipo del tipo di dati [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per il parametro in caso di specifica di una funzione di accesso a livello di codice.  
  
-   L'applicazione chiami codice **ICommandWithParameters:: GetParameterInfo** in modo che il provider possa ottenere il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipi di dati dei parametri in modo dinamico. Si noti che ciò determina un round trip aggiuntivo del server.  
  
> [!NOTE]  
>  Il provider non supporta la chiamata **ICommandWithParameters:: GetParameterInfo** per qualsiasi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] istruzione UPDATE o DELETE contenente una clausola FROM; per qualsiasi istruzione SQL in base a una sottoquery contenente i parametri. per le istruzioni SQL che contiene marcatori di parametro in entrambe le espressioni di un confronto, like o quantificato predicato; o query in cui uno dei parametri è un parametro a una funzione. Durante l'elaborazione di un batch di istruzioni SQL, il provider non supporta inoltre la chiamata **ICommandWithParameters:: GetParameterInfo** per i marcatori di parametro nelle istruzioni dopo la prima istruzione nel batch. Commenti (/ * \*/) non sono consentiti nel [!INCLUDE[tsql](../../../includes/tsql-md.md)] comando.  
  
 Il Driver OLE DB per SQL Server supporta i parametri di input nei comandi di istruzione SQL. Nei comandi delle chiamate a stored procedure, il Driver OLE DB per SQL Server supporta parametri di input, output e input/output. I valori dei parametri di output vengono restituiti all'applicazione in fase di esecuzione (solo se non sono stati restituiti set di righe) o quando tutti i set di righe restituiti vengono esauriti dall'applicazione. Per garantire che i valori restituiti siano validi, utilizzare **IMultipleResults** per forzare l'utilizzo di set di righe.  
  
 I nomi dei parametri delle stored procedure non devono essere specificati in una struttura DBPARAMBINDINFO. Utilizzare NULL per il valore della *pwszName* membro per indicare che il Driver OLE DB per SQL Server deve ignorare il nome del parametro e utilizzare solo l'ordinale specificato nel *rgParamOrdinals* appartenente  **ICommandWithParameters:: SetParameterInfo**. Se il testo del comando contiene parametri denominati e senza nome, tutti i parametri senza nome devono essere specificati prima di quelli denominati.  
  
 Se viene specificato il nome di un parametro di stored procedure, il Driver OLE DB per SQL Server controlla il nome per assicurarsi che sia valido. Il Driver OLE DB per SQL Server restituisce un errore quando riceve un nome di parametro errato dal consumer.  
  
> [!NOTE]  
>  Per esporre il supporto per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] XML e tipi definiti dall'utente (UDT), il Driver OLE DB per SQL Server implementa un nuovo [ISSCommandWithParameters](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md) interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [Comandi](../../oledb/ole-db-commands/commands.md)  
  
  

---
title: Parametri di comando | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- parameters [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, parameters
- SQL Server Native Client OLE DB provider, commands
- parameters [SQL Server Native Client], OLE DB
- commands [OLE DB]
ms.assetid: 072ead49-ebaf-41eb-9a0f-613e9d990f26
caps.latest.revision: 39
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cf00eb9d28acb7727b888eb065647184653b7e87
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168081"
---
# <a name="command-parameters"></a>Parametri dei comandi
  I parametri sono contrassegnati nel testo dei comandi dal carattere del punto interrogativo. L'istruzione SQL seguente è ad esempio contrassegnata per un solo parametro di input:  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 Per migliorare le prestazioni riducendo il traffico di rete, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non deduce automaticamente le informazioni sui parametri, a meno che **ICommandWithParameters:: GetParameterInfo** o  **ICommandPrepare:: Prepare** viene chiamato prima di eseguire un comando. Ciò significa che il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non automaticamente:  
  
-   Verificare la correttezza del tipo di dati specificato con **ICommandWithParameters:: SetParameterInfo**.  
  
-   Eseguire il mapping tra il valore DBTYPE specificato nelle informazioni relative all'associazione della funzione di accesso e il tipo di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] corretto per il parametro.  
  
 Se si specificano tipi di dati non compatibili con il tipo di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del parametro, è possibile che vengano ricevuti errori o che si verifichi una perdita della precisione con entrambi i metodi.  
  
 Per evitare che ciò si verifichi, è necessario:  
  
-   Assicurarsi che *pwszDataSourceType* corrisponde la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del tipo di dati per il parametro se hardcoded **ICommandWithParameters:: SetParameterInfo**.  
  
-   Assicurarsi che il valore DBTYPE associato al parametro sia dello stesso tipo del tipo di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per il parametro in caso di specifica di una funzione di accesso a livello di codice.  
  
-   Codificare l'applicazione di chiamare **ICommandWithParameters:: GetParameterInfo** in modo che il provider possa ottenere il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipi di dati dei parametri in modo dinamico. Si noti che ciò determina un round trip aggiuntivo del server.  
  
> [!NOTE]  
>  Il provider non supporta la chiamata **ICommandWithParameters:: GetParameterInfo** per qualsiasi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istruzione UPDATE o DELETE contenente una clausola FROM; per qualsiasi istruzione SQL una sottoquery contenente parametri; Per istruzioni SQL che contiene marcatori di parametro in entrambe le espressioni di un confronto, like o quantificato predicato; o query in cui uno dei parametri è un parametro a una funzione. Quando si elabora un batch di istruzioni SQL, il provider non supporta inoltre la chiamata **ICommandWithParameters:: GetParameterInfo** per i marcatori di parametro nelle istruzioni dopo la prima istruzione nel batch. Commenti (/ * \*/) non sono consentiti nel [!INCLUDE[tsql](../../includes/tsql-md.md)] comando.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta i parametri di input nei comandi di istruzione SQL. Sui comandi di chiamata di routine, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta parametri di input, output e input/output. I valori dei parametri di output vengono restituiti all'applicazione in fase di esecuzione (solo se non sono stati restituiti set di righe) o quando tutti i set di righe restituiti vengono esauriti dall'applicazione. Per garantire che i valori restituiti siano validi, utilizzare **IMultipleResults** per forzare l'utilizzo di set di righe.  
  
 I nomi dei parametri delle stored procedure non devono essere specificati in una struttura DBPARAMBINDINFO. Utilizzare NULL per il valore della *pwszName* membro per indicare che il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client deve ignorare il nome del parametro e utilizzare solo l'ordinale specificato nel *rgParamOrdinals*membro di **ICommandWithParameters:: SetParameterInfo**. Se il testo del comando contiene parametri denominati e senza nome, tutti i parametri senza nome devono essere specificati prima di quelli denominati.  
  
 Se viene specificato il nome di un parametro di stored procedure, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client controlla il nome per assicurarsi che sia valido. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce un errore quando riceve un nome di parametro errato dal consumer.  
  
> [!NOTE]  
>  Per esporre il supporto per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML e tipi definiti dall'utente (UDT), il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client implementa una nuova [ISSCommandWithParameters](../native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md) interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [Comandi](commands.md)  
  
  
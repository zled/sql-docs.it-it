---
title: Restrizioni sulle normali e connessioni di contesto | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: reference
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: 0c6fe4cb-d846-40b5-8884-35a9c770f5e8
caps.latest.revision: 24
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 290110b735765da45bca5f5f67bfd764f4abc6dc
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35694382"
---
# <a name="context-connections-and-regular-connections---restrictions"></a>Connessioni di contesto e connessioni normali - restrizioni
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In questo argomento vengono illustrate le restrizioni associate all'esecuzione di codice nel [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] processo tramite connessioni normali e di contesto.  
  
## <a name="restrictions-on-context-connections"></a>Restrizioni relative alle connessioni di contesto  
 Quando si sviluppa l'applicazione, tenere presenti le restrizioni seguenti che si applicano alle connessioni di contesto:  
  
-   È possibile tenere aperta una sola connessione di contesto per volta per una determinata connessione. Se vengono eseguite contemporaneamente più istruzioni in connessioni separate, ognuna di esse può avere la propria connessione di contesto. La restrizione non influisce sulle richieste simultanee provenienti da connessioni diverse ma solo su una specifica richiesta in una determinata connessione.  
  
-   Non è supportato il servizio MARS (Multiple Active Result Sets).  
  
-   Il **SqlBulkCopy** classe parti non funziona in una connessione di contesto.  
  
-   Non è supportata l'esecuzione di batch di aggiornamenti.  
  
-   **SqlNotificationRequest** non può essere utilizzato con comandi che vengono eseguiti su una connessione di contesto.  
  
-   Non è supportato l'annullamento di comandi che vengono eseguiti su una connessione di contesto. Il **SqlCommand.Cancel** metodo invisibile all'utente ignora la richiesta.  
  
-   Quando si utilizza "context connection=true", non è possibile utilizzare altre parole chiave della stringa di connessione.  
  
-   Il **SqlConnection.DataSource** proprietà restituirà null se la stringa di connessione per il **SqlConnection** è "connessione contesto = true", anziché il nome dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Impostazione di **SqlCommand. CommandTimeout** proprietà non ha effetto quando il comando viene eseguito su una connessione di contesto.  
  
## <a name="restrictions-on-regular-connections"></a>Restrizioni relative alle connessioni normali  
 Quando si sviluppa l'applicazione, tenere presenti le restrizioni seguenti che si applicano alle connessioni normali:  
  
-   Non è supportata l'esecuzione asincrona di comandi su server interni. Tra cui "async = true" nella stringa di connessione di un comando e quindi si esegue il comando, produce **System. NotSupportedException** generata. Viene visualizzato il messaggio "Asynchronous Processing non è supportato se eseguito in un processo [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]".  
  
-   **SqlDependency** oggetto non è supportato.  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione di contesto](../../../relational-databases/clr-integration/data-access/context-connection.md)  
  
  

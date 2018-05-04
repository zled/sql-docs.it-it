---
title: File di personalizzazione connettersi sezione | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connect section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: d50eb3cc-a822-486f-b80b-65bb50547ecd
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0835a305ce4e7c748c4b7a8c931a586f70d2bafa
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="customization-file-connect-section"></a>Collegare il File di personalizzazione
Il comportamento predefinito del gestore consiste nel negare tutte le connessioni. Il **connettersi** sezione specifica le eccezioni a questo comportamento. Ad esempio, se tutti i **connettersi** sezioni sono assenti o vuota, quindi per impostazione predefinita può essere eseguita alcuna connessione.  
  
 Il **connettersi** sezione può contenere:  
  
-   Una voce di accesso predefinita che specifica il valore predefinito lettura e scrittura di operazioni consentite in questa connessione. Se non è presente alcuna voce di accesso predefinita nella sezione, la sezione verrà ignorata.  
  
-   Nuova stringa di connessione che sostituisce la stringa di connessione client.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
 Una voce di accesso predefinito è nel formato:  
  
```  
  
Access=  
accessRight  
  
```  
  
 Una voce di stringa di connessione di sostituzione è nel formato:  
  
```  
  
Connect=  
connectionString  
  
```  
  
## <a name="remarks"></a>Osservazioni  
  
|Parte|Description|  
|----------|-----------------|  
|**Connetti**|Una stringa letterale che indica che si è una stringa di connessione.|  
|***connectionString***|Stringa che sostituisce la stringa di connessione client intero.|  
|**Accesso**|Una stringa letterale che indica che si è una voce di accesso.|  
|***accessRight***|Uno dei diritti di accesso seguenti:<br /><br /> -   **NoAccess** : utente non è possibile accedere all'origine dati.<br />-   **ReadOnly** , ovvero l'utente può leggere l'origine dati.<br />-   **ReadWrite** : utente può leggere o scrivere all'origine dati.|  
  
 Se si desidera consentire qualsiasi connessione (in disabilitando il comportamento del gestore predefinito), impostare la voce di accesso **connettersi predefinito** sezione a `Access=ReadWrite`ed eliminare o qualsiasi altro commento **connettersi** *identificatore* sezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Sezione Log File di personalizzazione](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Sezione relativa alla personalizzazione File SQL](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Sezione UserList File di personalizzazione](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Personalizzazione di DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Impostazioni Client richieste](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Informazioni sui File di personalizzazione](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Scrittura di un gestore personalizzato](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)




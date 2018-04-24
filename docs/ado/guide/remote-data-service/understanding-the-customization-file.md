---
title: Informazioni sui File di personalizzazione | Documenti Microsoft
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
- customization file in RDS [ADO]
ms.assetid: 136f74bf-8d86-4a41-be66-c86cbcf81548
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 72d44f46f3f6f1a349a2dabf7a0c7576d55fdfe7
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="understanding-the-customization-file"></a>Informazioni sui File di personalizzazione
Ogni intestazione di sezione nel file di personalizzazione è costituita da parentesi quadre (**[]**) contenente un parametro e tipo. I quattro tipi di sezioni sono indicati da stringhe letterali **connettersi**, **sql**, **userlist**, o **log**. Il parametro è il valore letterale stringa, il valore predefinito, un identificatore specificato dall'utente o nulla.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Pertanto, ogni sezione è contrassegnata con una delle intestazioni della sezione seguente:  
  
```  
  
[ connect default ] [ connect    
identifier   
] [ sql  default ] [ sql    
identifier   
] [ userlist    
identifier   
] [ logs ]  
  
```  
  
 Le intestazioni della sezione sono le parti seguenti.  
  
|Parte|Description|  
|----------|-----------------|  
|**connect**|Una stringa letterale che modifica una stringa di connessione.|  
|**sql**|Una stringa letterale che modifica una stringa di comando.|  
|**userlist**|Una stringa letterale che modifica i diritti di accesso di un utente specifico.|  
|**logs**|Valore letterale stringa che specifica un file di log errori di registrazione.|  
|**default**|Una stringa letterale che viene utilizzata alcun identificatore è specificato se trovato.|  
|*identifier*|Stringa che corrisponde a una stringa nel **connettersi** o **comando** stringa.<br /><br /> -Utilizzare questa sezione se contiene l'intestazione di sezione **connettersi** e la stringa dell'identificatore è stata trovata nella stringa di connessione.<br />-Utilizzare questa sezione se contiene l'intestazione di sezione **sql** e la stringa dell'identificatore è stata trovata nella stringa di comando.<br />-Utilizzare questa sezione se contiene l'intestazione di sezione **userlist** e la stringa dell'identificatore corrisponde un **connettersi** identificatore di sezione.|  
  
 Il **DataFactory** chiama il gestore, passando i parametri dei client. Il gestore esegue la ricerca di stringhe intere nei parametri del client corrispondenti agli identificatori nelle intestazioni della sezione appropriata. Se viene trovata una corrispondenza, il contenuto della sezione viene applicato al parametro del client.  
  
 Una particolare sezione viene utilizzata nelle seguenti circostanze:  
  
-   A **connettere** sezione viene utilizzata se la parte del valore del client di connettersi, parola chiave della stringa "**origine dati = * * * valore*", corrisponde a un **connettersi** identificatore sezione*.*  
  
-   Un **sql** sezione viene utilizzata se la stringa di comando del client contiene una stringa che corrisponde a un **sql** identificatore di sezione.  
  
-   Oggetto **connettersi** o **sql** sezione con un parametro predefinito viene utilizzato se è presente alcun identificatore corrispondente.  
  
-   Oggetto **userlist** sezione viene utilizzata se il **userlist** sezione identificatore corrisponde un **connettersi** identificatore di sezione. Se viene trovata una corrispondenza, il contenuto del **userlist** sezione vengono applicate alla connessione disciplinata il **connettersi** sezione.  
  
-   Se la stringa in una stringa di connessione o un comando corrisponde a quello in qualsiasi **connettersi** o **sql** sezione di intestazione e non esiste alcun **connettersi** o **sql**  sezione di intestazione con un parametro predefinito, la stringa del client viene usato senza alcuna modifica.  
  
-   Il **registri** sezione viene utilizzata ogni volta che il **DataFactory** è in esecuzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Collegare il File di personalizzazione](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Sezione Log File di personalizzazione](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Sezione relativa alla personalizzazione File SQL](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Sezione UserList File di personalizzazione](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Personalizzazione di DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Impostazioni Client richieste](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Scrittura di un gestore personalizzato](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)





















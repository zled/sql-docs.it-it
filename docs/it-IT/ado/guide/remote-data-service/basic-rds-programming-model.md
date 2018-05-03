---
title: Il modello di programmazione di servizi desktop remoto di base | Documenti Microsoft
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
- RDS programming model [ADO]
ms.assetid: 0bdd236b-edff-4aac-94c3-93e1465ca6c5
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 453a06af95c04695c2502180015d2f24d0d28b50
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="basic-rds-programming-model"></a>Modello di programmazione di base di servizi desktop remoto
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Servizi Desktop remoto indirizzi applicazioni presenti nell'ambiente: un'applicazione client specifica un programma che verrà eseguito su un server e i parametri necessari per restituire le informazioni desiderate. Il programma richiamato sul server ottiene accesso all'origine dati specificata, recupera le informazioni facoltativamente elabora i dati e quindi restituisce le informazioni risultanti all'applicazione client in un formato facilmente utilizzabile. Servizi Desktop remoto consente di eseguire la sequenza di azioni seguente:  
  
-   Specificare il programma che verrà richiamato nel server e ottenere un modo per farvi riferimento dal client. (Questo riferimento è a volte chiamato un *proxy*. Rappresenta il programma del server remoto. L'applicazione client "chiamerà" proxy come se fosse un programma locale, ma richiama effettivamente il programma del server remoto.)  
  
-   Richiamare il programma del server. Passare i parametri per l'applicazione server che identificano l'origine dati e il comando da eseguire. (L'applicazione server utilizza effettivamente ADO per accedere all'origine dati. ADO stabilisce una connessione con uno dei parametri specificati e quindi rilascia il comando specificato nel parametro other.)  
  
-   L'applicazione server Ottiene un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto dall'origine dati. Facoltativamente, il **Recordset** oggetto viene elaborato nel server.  
  
-   L'applicazione server restituisce finale **Recordset** oggetto all'applicazione client.  
  
-   Nel client, il **Recordset** oggetto viene inserito in un formato facilmente utilizzabile tramite controlli visivi.  
  
-   Tutte le modifiche per il **Recordset** oggetto vengono inviati all'applicazione server, che li usa per aggiornare l'origine dati.  
  
 Questo modello di programmazione contiene alcune funzionalità di praticità. Se non è necessaria un'applicazione server complessa per accedere all'origine dati e, se si forniscono le necessarie per la connessione e i parametri di comando, servizi desktop remoto verrà automaticamente recuperare i dati specificati con un semplice programma server predefinito.  
  
 Se è necessaria un'elaborazione più complessa, è possibile specificare un'applicazione server personalizzata. Ad esempio, poiché le potenzialità di ADO a sua disposizione dispone di un'applicazione server personalizzata, Impossibile connettersi a più origini dati diverse, combinare i dati in qualche modo complesso e quindi restituire un risultato semplice, elaborato per l'applicazione client.  
  
 Infine, se le proprie esigenze in un punto intermedio, ADO supporta ora la personalizzazione del comportamento del programma server predefinito.  
  
## <a name="see-also"></a>Vedere anche  
 [Modello di programmazione di servizi desktop remoto in modo dettagliato](../../../ado/guide/remote-data-service/rds-programming-model-in-detail.md)   
 [Scenario di servizi desktop remoto](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [Esercitazione di servizi desktop remoto](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Utilizzo e sicurezza per RDS](../../../ado/guide/remote-data-service/rds-usage-and-security.md)



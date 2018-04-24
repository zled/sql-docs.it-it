---
title: Personalizzazione di DataFactory | Documenti Microsoft
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
- DataFactory customization in RDS [ADO]
ms.assetid: 86d77985-a0d0-405a-8587-c85a20540a0e
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6926c858ca9b1f8c09014b8637c8a17c6ca33f7b
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="datafactory-customization"></a>Personalizzazione di DataFactory
Remote Data Service (RDS) fornisce un modo per accedere facilmente ai dati in un sistema client/server a tre livelli. Un controllo di dati client specifica i parametri della stringa di connessione e comando per eseguire una query su un'origine dati remota o una stringa di connessione e [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) parametri per eseguire un aggiornamento dell'oggetto.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 I parametri vengono passati a un'applicazione server, che esegue l'operazione di accesso ai dati nell'origine dati remota. Servizi Desktop remoto offre un programma server predefinito denominato il [RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) oggetto. Il **RDSServer** restituisce qualsiasi **Recordset** oggetto generato da una query al client.  
  
 Tuttavia, il **RDSServer** è limitato all'esecuzione di query e aggiornamenti. Non può eseguire qualsiasi convalida o elaborazione sulle stringhe di connessione o un comando.  
  
 Con ADO, è possibile specificare che il **DataFactory** funzionano in combinazione con un altro tipo di programma server denominato un *gestore*. Il gestore può modificare le stringhe di comando e di connessione client prima che vengano utilizzate per accedere all'origine dati. Inoltre, il gestore può applicare i diritti di accesso, che regolano la capacità del client per leggere e scrivere i dati all'origine dati.  
  
 I parametri a cui che il gestore utilizza per modificare i parametri di client e i diritti di accesso vengono specificati nelle sezioni di un file di personalizzazione.  
  
 Gli argomenti seguenti forniscono ulteriori informazioni sulla personalizzazione di **DataFactory** oggetto.  
  
-   [Informazioni sul file di personalizzazione](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)  
  
-   [Sezione sulla connessione del file di personalizzazione](../../../ado/guide/remote-data-service/customization-file-connect-section.md)  
  
-   [Sezione SQL del file di personalizzazione](../../../ado/guide/remote-data-service/customization-file-sql-section.md)  
  
-   [Sezione UserList del file di personalizzazione](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)  
  
-   [Sezione Logs del file di personalizzazione](../../../ado/guide/remote-data-service/customization-file-logs-section.md)  
  
-   [Impostazioni obbligatorie dei client](../../../ado/guide/remote-data-service/required-client-settings.md)  
  
-   [Scrittura di un gestore personalizzato](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)



---
title: Sezione UserList del File di personalizzazione | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- UserList section in rds [ADO]
- customization file in RDS [ADO]
ms.assetid: 42e8ec20-eaac-4a95-8cb8-4bba93a75bcb
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dcf8649af2695fa354659f13e891521eb14f39cb
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273830"
---
# <a name="customization-file-userlist-section"></a>Sezione UserList File di personalizzazione
Il **userlist** sezione riguarda il **connettersi** sezione con la stessa sezione *identificatore* parametro.  
  
 In questa sezione può contenere un *voce di accesso utente*, che specifica l'accesso i diritti per l'utente specificato ed esegue l'override di *predefinito* *accedere voce* in corrispondenti**connettersi** sezione.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
 Una voce di accesso utente è nel formato:  
  
 *userName* **=**   
 ***accessRights***  
  
|Parte|Description|  
|----------|-----------------|  
|*userName*|Il *nome utente* della persona che utilizza la connessione. Nomi utente validi sono definiti con IIS **Service Manager** finestra di dialogo.|  
|***accessRights***|Uno dei diritti di accesso seguenti:<br /><br /> -   **NoAccess** : utente non è possibile accedere all'origine dati.<br />-   **ReadOnly** , ovvero l'utente può leggere l'origine dati.<br />-   **ReadWrite** : utente può leggere o scrivere all'origine dati.|  
  
## <a name="see-also"></a>Vedere anche  
 [Collegare il File di personalizzazione](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Sezione Log File di personalizzazione](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Sezione relativa alla personalizzazione File SQL](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Personalizzazione di DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Impostazioni Client richieste](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Informazioni sui File di personalizzazione](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Scrittura di un gestore personalizzato](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)



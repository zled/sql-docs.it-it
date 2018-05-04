---
title: Matrice di compatibilità | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- driver compatibility issues [ODBC]
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
- application compatibility issues [ODBC]
- application upgrades [ODBC], compatibility matrix
- upgrading applications [ODBC], compatibility matrix
ms.assetid: 0690b463-15a1-48fa-9d0b-9cc9e5bf7fc6
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ce98e3471f3bf14ada77fcbb67291ba8a4dff166
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="compatibility-matrix"></a>Matrice di compatibilità
Nella tabella seguente viene descritta la compatibilità dei tipi di applicazioni e driver definite in precedenza in questa sezione.  
  
|Tipo di applicazione<br /><br /> e versione|ODBC a 32 bit<br /><br /> 2.*x* driver|ODBC 3. *x*<br /><br /> Driver|Driver ODBC 3.8|ISO e aprire compatibile con gruppo di driver|  
|--------------------------------------|-----------------------------------|---------------------------|---------------------|-----------------------------------------|  
|applicazione a 16 bit, qualsiasi versione|Compatibilità|Compatibilità|Compatibilità|Compatibilità|  
|2 pure. *x* applicazione|Compatibilità|Compatibilità|Compatibilità|Non compatibile con [3]|  
|2 pure. *x* ricompilare l'applicazione|Compatibilità|Compatibile [1]|Compatibile [1]|Non compatibile con [3]|  
|2 pure. *x* applicazione Unicode|Compatibilità|Compatibile [1]|Compatibile [1]|Non compatibile con [3]|  
|Applicazione di gruppo aprire puro e conforme a ISO|Non è compatibile|Compatibile [2]|Compatibile [2]|Compatibile [2]|  
|Applicazione 3.0|Non è compatibile|Compatibilità|Compatibilità|Non compatibile con [4]|  
|Applicazione 3.5 pure|Non è compatibile|Compatibilità|Compatibilità|Non compatibile con [4]|  
|Applicazione 3.8 (o versione successiva)|Non compatibile con [5]|Non compatibile con [5]|Compatibilità|Non compatibile con [4]|  
|Applicazione sostituito|Compatibilità|Compatibilità|Compatibilità|Non compatibile con [3]|  
  
 [1] l'applicazione è necessario ricompilare utilizzando le intestazioni ODBC 3.5 (o versione successive) con l'opzione di UNICODE (se si tratta di un'applicazione Unicode) e deve impostare ODBCVER 0x0250.  
  
 [2] l'applicazione deve compilare l'utilizzo di intestazioni ODBC 3.5 (o versione successive) e collegare con gestione Driver ODBC. Inoltre necessario impostare il flag di intestazione ODBC_STD.  
  
 [3] con questa configurazione può potenzialmente non funzionerà perché non esistono funzionalità in ODBC 2. *x* che non sono presenti gli standard, ad esempio i segnalibri.  
  
 [4] questa configurazione potrebbero non riuscire a funzionare poiché sono presenti funzionalità in ODBC 3*x* che non sono presenti gli standard, ad esempio i segnalibri.  
  
 [5] questa configurazione potrebbero non riuscire perché sono presenti funzionalità che non sono presenti nel driver ODBC a 2. x o 3. x, ad esempio specifici del driver ODBC 3.8 [tipi di dati C in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
## <a name="driver-manager-compatibility"></a>Compatibilità di Gestione driver  
 Un'applicazione ODBC 3.0 che deve funzionare con tutte le versioni di gestione Driver deve eseguire le operazioni seguenti all'avvio:  
  
-   Allocare un handle di ambiente.  
  
-   Impostare l'attributo di ambiente SQL_ATTR_ODBC_VERSION SQL_OV_ODBC3_80. Se la gestione Driver restituisce SQL_ERROR, gestione Driver è meno recente 3.8. Ripristinare SQL_ATTR_ODBC_VERSION SQL_OV_ODBC3 o SQL_OV_ODBC2, come appropriato, in modo che corrisponda al Driver Manager.  
  
-   Allocare un handle di connessione.  
  
-   Stabilire una connessione.  
  
-   Chiamare SQLGetInfo per SQL_DRIVER_ODBC_VER determinare la versione del driver. Se il driver è un driver ODBC 3.8, è possibile utilizzare tipi C specifici del driver. In caso contrario, non utilizzare tipi di dati C specifici del driver.  
  
 Si noti che un'applicazione di 3. x ricompilata ODBC è possibile utilizzare funzioni ODBC 3.8 diversi dai tipi C specifici del driver senza specificare SQL_OV_ODBC3_80 per SQL_ATTR_ODBC_VERSION. È simile a un'applicazione di 2. x ODBC ricompilata utilizzando funzioni ODBC 3. x.  
  
## <a name="using-sqlcancelhandle-in-an-application-compatible-with-all-driver-managers"></a>Utilizzo di SQLCancelHandle in un'applicazione compatibile con tutti i gestori di Driver  
 Poiché [SQLCancelHandle funzione](../../../odbc/reference/syntax/sqlcancelhandle-function.md) non è supportata in Gestioni di Driver che sono stati rilasciati prima di Windows 7, non è possibile caricare un'applicazione nelle versioni precedenti di Windows se chiama **SQLCancelHandle** direttamente. Per elaborare tutte le versioni dei Driver Manager e utilizzare **SQLCancelHandle** nelle nuove versioni di Windows, un'applicazione deve chiamare **SQLCancelHandle** indirettamente tramite **LoadLibrary** e **GetProcAddress.**  
  
## <a name="see-also"></a>Vedere anche  
 [Novità di ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md)

---
title: Scenario di servizi desktop remoto | Documenti Microsoft
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
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: a7dcad87-aaf0-4b02-9660-472f8469761c
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d1fef484f86a7558ab77159b4273c4d2065892fe
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="rds-scenario"></a>Scenario di servizi desktop remoto
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 L'applicazione Address Book è uno scenario che illustra come usare Remote Data Service (RDS) per compilare un'applicazione Web semplice, compatibile con i dati, ovvero una rubrica della società online. Questo scenario è utile per Microsoft Visual Basic, Scripting Edition (VBScript) e i programmatori COM che desiderano informazioni su come utilizzare i controlli ActiveX che supportano i dati con Servizi Desktop remoto per il software più esperto gli sviluppatori che desiderano creare applicazioni Web incentrate sui dati.  
  
 Questo scenario si presuppone che si sapere come utilizzare il tag di layout HTML basic, le tecniche di associazione di dati di utilizzo DHTML e programma con i controlli ActiveX.  
  
 Se è stato installato il SDK, il codice sorgente completo per l'applicazione di esempio Address Book è reperibile nella directory SDK in samples\dataaccess\rds\AddressBook\AddressBook.asp. Per visualizzare lo scenario di Address Book, in Internet Explorer 4.0 o versione successiva, digitare **http://*webserver*/RDS/AddressBook/AddressBook.asp** in *webserver* è il nome specificato nel computer server di Windows NT 4.0 o Windows 2000 Web che esegue Internet Information Services (IIS) e ASP.  
  
## <a name="introduction-to-address-book"></a>Introduzione alla Rubrica  
 L'applicazione di esempio Address Book fornisce una rubrica online semplice che è possibile utilizzare per la pubblicazione di una directory di ricerca su una rete intranet. La Rubrica è progettata in modo che un utente può immettere una stringa di ricerca in uno o più campi per richiedere informazioni sui dipendenti. Per visualizzare le funzionalità di base del servizio dati remota, l'applicazione di esempio viene mantenuta intenzionalmente piccolo, con un numero minimo di oggetti e i campi di ricerca.  
  
 L'interfaccia dell'applicazione è costituita dalle parti seguenti:  
  
-   Non visivi **RDS. DataControl** oggetto di associazione di dati utilizzato dal client per connettersi al database.  
  
-   Criteri di ricerca di caselle di testo HTML che agiscono come campi di input per l'attributo dipendente.  
  
-   HTML pulsanti di comando di compilazione di query, cancellare i campi di ricerca, aggiornare il database con informazioni sui dipendenti, annullare le modifiche in sospeso e passare le righe di dati visualizzati nella griglia.  
  
-   Associazione dati DHTML per visualizzare i dati restituiti dalle query in un database back-end (tramite il **RDS. DataControl** oggetto con associazione a dati) in una tabella.  
  
-   Routine di VBScript che si connettono a ognuno degli elementi che sono stati indicati in precedenza e consentano loro di interagire. Il codice VBScript viene inoltre utilizzato per inizializzare il **RDS. DataControl** dell'oggetto e creare in modo dinamico le intestazioni di colonna nella tabella HTML dai nomi di **RDS. DataControl** i campi del recordset.  
  
 Seguire i collegamenti del passaggio per passaggio per impostare ed eseguire lo scenario e per ulteriori informazioni sulle modalità di funzionamento dello scenario.  
  
 Questo scenario contiene gli argomenti seguenti.  
  
-   [Requisiti di sistema per l'applicazione Address Book](../../../ado/guide/remote-data-service/system-requirements-for-the-address-book-application.md)  
  
-   [Esecuzione dello script SQL per Address Book](../../../ado/guide/remote-data-service/running-the-address-book-sql-script.md)  
  
-   [Esecuzione dell'applicazione di esempio Address Book](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)  
  
-   [Oggetto di data binding di Address Book](../../../ado/guide/remote-data-service/address-book-data-binding-object.md)  
  
-   [Pulsanti di comando di Address Book](../../../ado/guide/remote-data-service/address-book-command-buttons.md)  
  
-   [Pulsanti di spostamento di Address Book](../../../ado/guide/remote-data-service/address-book-navigation-buttons.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Requisiti di sistema per l'applicazione Address Book](../../../ado/guide/remote-data-service/system-requirements-for-the-address-book-application.md)   
 [Microsoft ActiveX Data Objects (ADO)](../../../ado/microsoft-activex-data-objects-ado.md)   
 [Nozioni di base di servizi desktop remoto](../../../ado/guide/remote-data-service/rds-fundamentals.md)   
 [Esercitazione su RDS](../../../ado/guide/remote-data-service/rds-tutorial.md)



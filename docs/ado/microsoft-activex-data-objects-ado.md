---
title: Microsoft ActiveX Data Objects (ADO) | Documenti Microsoft
ms.custom: 
ms.date: 07/25/2017
ms.reviewer: 
ms.suite: 
ms.prod: sql-non-specified
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ADO, about
ms.assetid: 2fa6237b-44b8-4b6c-9952-5acd80a54e20
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 28fa2c279cfd7964d8516514a3caed129e335692
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="microsoft-activex-data-objects-ado"></a>Microsoft ActiveX Data Objects (ADO)

ADO viene utilizzato nei programmi C++ per connettersi a SQL Server. Naturalmente, funziona anche per connettersi al Database SQL di Azure nel cloud.

In ogni sezione di questo articolo descrive un componente di ADO.

> [!NOTE]
> ADO.NET è diverso da quello di ADO. Vengono descritti ADO.NET e molti altri driver di connessione SQL e delle lingue, a partire da [driver SQL Server](../connect/sql-connection-libraries.md).

  
## <a name="ado"></a>ADO  
 Microsoft ActiveX Data Objects (ADO) consentono alle applicazioni client accedere e modificare i dati da una varietà di origini tramite un provider OLE DB. Due vantaggi principali sono: semplicità di utilizzo, ad alta velocità, overhead di memoria ridotto e un footprint di disco di piccole dimensioni. ADO supporta le funzionalità principali per la creazione di client/server e applicazioni basate sul Web.  
  
## <a name="ado-md"></a>ADO MD  
 Microsoft ActiveX Data Objects (ADO MD) (multidimensionale) consente di accedere ai dati multidimensionali da linguaggi, ad esempio Microsoft Visual Basic e Microsoft Visual C++. ADO MD estende Microsoft ActiveX Data Objects (ADO) per includere gli oggetti specifici di dati multidimensionali, ad esempio gli oggetti CubeDef e set di celle. Con ADO MD è Sfoglia schema multidimensionale, un cubo di query e recuperare i risultati.  
  
 Ad esempio ADO, ADO MD utilizza un provider OLE DB sottostante per ottenere l'accesso ai dati. Per utilizzare ADO MD, il provider deve essere un provider di dati multidimensionali (dati Multidimensionali), come definito da OLE DB per OLAP. I provider di dati multidimensionali presentano i dati in visualizzazioni multidimensionali invece dati tabulari dei provider di dati presenti in visualizzazioni tabulari. Consultare la documentazione per il provider OLE DB OLAP per informazioni più dettagliate sulla sintassi specifica e i comportamenti supportati dal provider.  
  
## <a name="rds"></a>SERVIZI DESKTOP REMOTO  
 Remote Data Service (RDS) è una funzionalità di ADO, con cui si spostano dati da un server a un'applicazione client o di una pagina Web, modificare i dati nel client e restituire gli aggiornamenti al server in un unico round trip.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="adox"></a>ADOX  
 Microsoft ActiveX Data Objects Extensions per Data Definition Language e protezione (ADOX) è un'estensione agli oggetti ADO e modello di programmazione. ADOX include oggetti per la creazione di schemi e modifica, nonché protezione. Poiché si tratta di un approccio basato su oggetti per modificare lo schema, è possibile scrivere codice che funzionerà con dati di varie origini indipendentemente dalle differenze nelle loro sintassi native.  
  
 ADOX è una libreria complementare agli oggetti ADO principali. Espone oggetti aggiuntivi per la creazione, modifica ed eliminazione di oggetti dello schema, ad esempio tabelle e procedure. Include anche gli oggetti di sicurezza per gestire utenti e gruppi e concedere e revocare le autorizzazioni per gli oggetti.  
  
## <a name="documentation"></a>Documentazione  
 [Problemi di progettazione di sicurezza ADO](../ado/guide/ado-security-design-issues.md)  
  
 [Manuale del programmatore ADO](../ado/guide/ado-programmer-s-guide.md)  
  
 Introduzione all'utilizzo di ADO, RDS, ADO MD e ADOX.  
  
 [Riferimento del programmatore ADO](../ado/reference/ado-programmer-s-reference.md)  
  
 In questa sezione della documentazione di ADO contiene argomenti per ogni ADO, RDS, ADO MD e ADOX oggetto, insieme, proprietà, proprietà dinamiche, metodo, evento ed enumerazione.  
  
 [Glossario di ADO](../ado/ado-glossary.md)  
  
## <a name="support"></a>Supporto  
 Libera della Guida con problemi di ADO, ripetere la registrazione al newsgroup pubblico ADO. Questo newsgroup viene monitorato dal personale del supporto Microsoft (tecnico) che coprono ADO e da altri sviluppatori esperti di ADO.  
  
 Ulteriori informazioni sulle opzioni di supporto sono reperibile nel sito di Microsoft Help Web e supporto tecnico.




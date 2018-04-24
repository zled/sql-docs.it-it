---
title: Esercitazione su RDS | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO]
ms.assetid: 6e3305a0-7bc7-40d1-9122-235c15d23ab2
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 29839e451deb37b1c4b9bac4a963dda36cf5b597
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="rds-tutorial"></a>Esercitazione di servizi desktop remoto
In questa esercitazione viene illustrato l'utilizzo del modello di programmazione di servizi desktop remoto per eseguire query e aggiornare un'origine dati. In primo luogo, descrive i passaggi necessari per completare questa attività. Nell'esercitazione viene quindi ripetuta in Microsoft® Visual Basic Scripting Edition (dotato di ADO per Windows Foundation Classes (ADO/WFC)).  
  
 In questa esercitazione viene codificata in linguaggi diversi per due motivi:  
  
-   La documentazione relativa a Servizi Desktop remoto si presuppone che i codici di lettura in Visual Basic. In questo modo la documentazione utile per i programmatori Visual Basic, ma è meno utile per i programmatori che utilizzano altri linguaggi.  
  
-   Se non si è sicuri su una particolare funzionalità di servizi desktop remoto e dispone di un altro linguaggio, potrebbe essere in grado di risolvere la domanda cercando la stessa funzionalità in un altro linguaggio.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="how-the-tutorial-is-presented"></a>La modalità di presentazione dell'esercitazione  
 Questa esercitazione è basata sul modello di programmazione di servizi desktop remoto. Viene descritto ogni passaggio del modello di programmazione singolarmente. Inoltre, viene illustrato come ciascuno di essi con un frammento di codice Visual Basic.  
  
 L'esempio di codice viene ripetuto in altri linguaggi discussione minimo. Ogni passaggio in un'esercitazione sul linguaggio di programmazione specificato è contrassegnato con il passaggio corrispondente nel modello di programmazione ed esercitazione descrittiva. Utilizzare il numero del passaggio per riferimento alla trattazione nell'esercitazione descrittiva.  
  
 Il modello di programmazione di servizi desktop remoto è indicato nella sezione seguente. Utilizzarlo come una Guida di orientamento mentre si esegue l'esercitazione.  
  
## <a name="rds-programming-model-with-objects"></a>Modello di programmazione di servizi desktop remoto con gli oggetti  
  
-   Specificare il programma che verrà richiamato nel server e ottenere un modo (proxy) per farvi riferimento dal client.  
  
-   Richiamare il programma del server. Parametri passati all'applicazione server che identifica l'origine dati e il comando da eseguire.  
  
-   L'applicazione server Ottiene un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto dall'origine dati, in genere utilizzando ADO. Facoltativamente, il **Recordset** oggetto viene elaborato nel server.  
  
-   L'applicazione server restituisce finale **Recordset** oggetto all'applicazione client.  
  
-   Nel client, il **Recordset** oggetto facoltativamente viene inserito in un formato facilmente utilizzabile tramite controlli visivi.  
  
-   Diventa il **Recordset** oggetto vengono inviati al server e utilizzato per aggiornare l'origine dati.  
  
 Questa esercitazione contiene gli argomenti seguenti.  
  
-   [Passaggio 1: Specificare un programma del server (esercitazione su RDS)](../../../ado/guide/remote-data-service/step-1-specify-a-server-program-rds-tutorial.md)  
  
-   [Passaggio 2: Richiamare il programma del server (esercitazione su RDS)](../../../ado/guide/remote-data-service/step-2-invoke-the-server-program-rds-tutorial.md)  
  
-   [Passaggio 3: Il server ottiene un recordset (esercitazione su RDS)](../../../ado/guide/remote-data-service/step-3-server-obtains-a-recordset-rds-tutorial.md)  
  
-   [Passaggio 4: Il server restituisce il recordset (esercitazione su RDS)](../../../ado/guide/remote-data-service/step-4-server-returns-the-recordset-rds-tutorial.md)  
  
-   [Passaggio 5: L'oggetto DataControl viene reso utilizzabile (esercitazione su RDS)](../../../ado/guide/remote-data-service/step-5-datacontrol-is-made-usable-rds-tutorial.md)  
  
-   [Passaggio 6: Le modifiche vengono inviate al server (esercitazione su RDS)](../../../ado/guide/remote-data-service/step-6-changes-are-sent-to-the-server-rds-tutorial.md)  
  
-   [Esercitazione su RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Passaggio 1: Specificare un'applicazione Server (esercitazione di servizi desktop remoto)](../../../ado/guide/remote-data-service/step-1-specify-a-server-program-rds-tutorial.md)   
 [Esercitazione su RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   

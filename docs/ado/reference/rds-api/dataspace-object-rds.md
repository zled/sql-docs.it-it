---
title: Oggetto DataSpace (RDS) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- DataSpace object [RDS]
ms.assetid: 9194bffa-5bdf-4dff-af86-f7158c23bfa7
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3c4ee2e71334998cd0d2cba1c0c52c67e3314619
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="dataspace-object-rds"></a>Oggetto DataSpace (RDS)
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Crea proxy sul lato client per oggetti di business personalizzata che si trovano nel livello intermedio.  
  
 Remote Data Service deve proxy degli oggetti business in modo che i componenti lato client possono comunicare con gli oggetti business che si trova nel livello intermedio. I proxy semplificano la creazione di pacchetti, disassemblaggio e di trasporto (marshalling) dell'applicazione [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) dati oltre i limiti di processo o del computer.  
  
 Remote Data Service utilizza la **RDS. DataSpace** dell'oggetto [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) metodo per creare i proxy degli oggetti business. Il proxy dell'oggetto business viene creato dinamicamente ogni volta che viene creata un'istanza della relativa controparte oggetto business di livello intermedio. Remote Data Service supporta i seguenti protocolli: HTTP, HTTPS (HTTP Secure Sockets), DCOM e in-process (componenti client e l'oggetto business si trovano nello stesso computer).  
  
> [!NOTE]
>  Servizi Desktop remoto si comporta in modo "senza stato" quando il **RDS. DataSpace** oggetto utilizza il protocollo HTTP o HTTPS. Vale a dire le informazioni relative a una richiesta client interne viene eliminate dopo che il server ha restituito una risposta.  
  
> [!NOTE]
>  Anche se l'oggetto business sembra esiste per la durata del proxy dell'oggetto business, l'oggetto business esista effettivamente solo fino a quando non viene inviata una risposta a una richiesta. Quando viene emessa una richiesta (vale a dire, viene richiamato un metodo per l'oggetto business), il proxy apre una nuova connessione al server e il server crea una nuova istanza dell'oggetto business. Dopo l'oggetto business risponde alla richiesta, il server Elimina definitivamente l'oggetto business e chiude la connessione.  
  
> [!NOTE]
>  Questo comportamento significa che non è possibile passare i dati da una richiesta a un altro utilizzando una proprietà dell'oggetto business o una variabile. È necessario utilizzare un altro meccanismo, ad esempio un file o un argomento del metodo, per rendere persistenti i dati.  
  
 L'ID di classe per il **RDS. DataSpace** oggetto è 0-983A-00C04FC29E36 BD96C556 65A3 - 11 D.  
  
 Il **DataSpace** oggetto è sicuro per lo script.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi dell'oggetto DataSpace (Servizi Desktop remoto)](../../../ado/reference/rds-api/dataspace-object-rds-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di oggetto DataSpace e metodo CreateObject (VBScript)](../../../ado/reference/rds-api/dataspace-object-and-createobject-method-example-vbscript.md)



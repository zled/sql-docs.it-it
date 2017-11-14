---
title: Garantire sufficiente spazio di TempDB | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TempDB space in RDS [ADO]
ms.assetid: 09130db1-6248-4234-a1e5-a9c8e1622c06
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 32f05f84953b09f4d727fe6bcba7b4230825faa2
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="ensuring-sufficient-tempdb-space"></a>Garantire sufficiente spazio di TempDB
Se si verificano errori durante la gestione [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) gli oggetti che è necessario spazio di elaborazione su Microsoft SQL Server 6.5, potrebbe essere necessario aumentare le dimensioni del database TempDB. (Alcune query richiedono spazio di elaborazione temporaneo, ad esempio, una query con una clausola ORDER BY richiede un ordinamento del **Recordset**, che richiede spazio temporaneo.)  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
> [!IMPORTANT]
>  Leggere questa procedura prima di eseguire le azioni, perché non è facile compattare un dispositivo quando viene espanso.  
  
> [!NOTE]
>  InMicrosoft predefinita SQL Server 7.0 e versioni successive, TempDB impostazione è di aumentare automaticamente in base alle esigenze. Pertanto, questa procedura può essere solo necessaria per i server che eseguono versioni precedenti alla 7.0.  
  
### <a name="to-increase-the-tempdb-space-on-sql-server-65"></a>Per aumentare lo spazio di TempDB in SQL Server 6.5  
  
1.  Avviare Microsoft SQL Server Enterprise Manager, aprire la struttura ad albero per il Server e quindi aprire la struttura ad albero di dispositivi di Database.  
  
2.  Selezionare un dispositivo (fisico) per espandere, ad esempio Master e fare doppio clic sul dispositivo per aprire la **Edit Database Device** la finestra di dialogo.  
  
     Questa finestra di dialogo Mostra la quantità di spazio utilizzano i database correnti.  
  
3.  Nel **dimensioni** casella, aumentare il dispositivo nella quantità desiderata (ad esempio, 50 megabyte (MB) di spazio su disco rigido).  
  
4.  Fare clic su **Change Now** per aumentare la quantità di spazio in cui è possibile espandere il database TempDB (logico).  
  
5.  Aprire la struttura di database nel server e quindi fare doppio clic su **TempDB** per aprire la **Modifica Database** la finestra di dialogo. Il **Database** scheda indica la quantità di spazio attualmente allocato a TempDB (**dimensioni dei dati**). Per impostazione predefinita, questo è 2 MB.  
  
6.  Sotto il **dimensioni** gruppo, fare clic su **Espandi**. I grafici seguenti mostrano lo spazio disponibile e viene allocato in ognuno dei dispositivi fisici. Le barre in bordeaux rappresentano lo spazio disponibile.  
  
7.  Selezionare un **Log dispositivo**, ad esempio Master, per visualizzare le dimensioni disponibili nel **dimensioni (MB)** casella.  
  
8.  Fare clic su **espandere ora** per allocare lo spazio nel database TempDB.  
  
     Il **Modifica Database** la finestra di dialogo consente di visualizzare la nuova dimensione allocata per il database TempDB.  
  
 Per ulteriori informazioni su questo argomento, cercare il file della Guida di Microsoft SQL Server Enterprise Manager per "Finestra di dialogo espandere Database".  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali su RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)




---
title: Contrassegnare gli oggetti Business come sicuri per lo Scripting | Documenti Microsoft
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
helpviewer_keywords:
- business objects in RDS [ADO]
ms.assetid: 0be98d1a-ab3d-4dce-a166-dacda10d154a
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2e9e400052e9c3cb794089d1731d42abd6feca37
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="marking-business-objects-as-safe-for-scripting"></a>Contrassegnare gli oggetti Business come sicuri per lo Scripting
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Per garantire un ambiente sicuro di Internet, è necessario contrassegnare tutti gli oggetti business con il [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) dell'oggetto [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) metodo come "sicuri per lo script". È necessario verificare che siano contrassegnati come tale nell'area di licenza del Registro di sistema prima di poter essere usati in DCOM.  
  
> [!NOTE]
>  Gli oggetti business contrassegnati come "sicuri per lo script" o per l'inizializzazione possono viene creata un'istanza e inizializzati da chiunque attraverso la rete. Contrassegnare un oggetto business "sicuri per lo script" non lo rende sicuro. È estremamente importante assicurarsi che gli oggetti business sono codificati con la massima sicurezza per garantire che tali oggetti non rappresentano un punto di accesso protetto per i dati sensibili.  
  
 Per contrassegnare manualmente gli oggetti business come sicuri per lo script, creare un file di testo con estensione reg contenente il testo seguente. In questo esempio, \< *MyActiveXGUID*> è il numero esadecimale GUID dell'oggetto business. I seguenti due numeri abilitare la funzionalità di sicurezza per lo scripting:  
  
```  
[HKEY_CLASSES_ROOT\CLSID\<MyActiveXGUID>\Implemented   
Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}]  
[HKEY_CLASSES_ROOT\CLSID\<MyActiveXGUID>\Implemented   
Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}]  
```  
  
 Salvare il file e unirlo del Registro di sistema utilizzando l'Editor del Registro di sistema o fare doppio clic sul file con estensione reg in Esplora risorse.  
  
 Gli oggetti business creati in Microsoft Visual Basic possono essere contrassegnati automaticamente come "sicuri per lo script" con il pacchetto e distribuzione guidata. Quando viene richiesto di specificare le impostazioni di sicurezza, selezionare **sicure per l'inizializzazione** e **sicuri per lo script**.  
  
 Nell'ultimo passaggio, l'applicazione Installazione guidata crea un file. htm e un file con estensione cab. È quindi possibile copiare questi due file al computer di destinazione e fare doppio clic sul file htm per caricare la pagina e registrare correttamente il server.  
  
 Poiché per impostazione predefinita, l'oggetto business verrà installato nella directory Windows\System32\Occache spostarlo nella directory Windows\System32 e modificare il **HKEY_CLASSES_ROOT\CLSID\\**  \< *MyActiveXGUID*>\\**InprocServer32** chiave del Registro di sistema in base al percorso corretto.



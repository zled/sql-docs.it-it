---
title: Impostazioni (caricamento di oggetti) del progetto (AccessToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-access
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 9ec1c1e8-a3e1-4e81-bf49-631f87daa209
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: e81759865b5d0356f89584390d10610c43154151
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="project-settings-loading-objects-accesstosql"></a>Impostazioni (caricamento di oggetti) del progetto (AccessToSQL)
Le impostazioni di progetto durante il caricamento di oggetti consentono di configurare come oggetti di database di Access vengono sincronizzati con gli oggetti di database di SQL Server.  
  
Le azioni predefinite specificano le impostazioni predefinite per l'aggiornamento di oggetti dal database di Access e per la sincronizzazione degli oggetti con il database di SQL Server. Per altre informazioni, vedere [aggiornamento dal Database di &#40;AccessToSQL&#41;](../../ssma/access/refresh-from-database-accesstosql.md)  
  
È possibile accedere a due diverse pagine di sincronizzazione che contengono le stesse impostazioni:  
  
-   Per specificare impostazioni per tutti i progetti futuri di SSMA, il **strumenti** menu, fare clic su **DefaultProject impostazioni**e quindi fare clic su **durante il caricamento di oggetti** nella parte inferiore del riquadro a sinistra.  
  
-   Per specificare le impostazioni per il progetto corrente, il **strumenti** menu, fare clic su **impostazioni progetto**e quindi fare clic su **durante il caricamento di oggetti** nella parte inferiore del riquadro a sinistra.  
  
## <a name="options"></a>Opzioni  
  
##### <a name="misc"></a>Varie  
  
##### <a name="attempts"></a>Tentativi  
Fornisce le informazioni sul numero di passaggi di rendere gli oggetti da caricare in SQL Server. Caricamento degli oggetti in SQL Server viene in genere eseguito in più passaggi. Gli oggetti che non riescono a caricare il primo passaggio, ad esempio le chiavi esterne, potrebbero caricare correttamente il passaggio successivo.  
  
Per impostazione predefinita il valore è 2.  
  
## <a name="synchronization-for-sql-server"></a>Sincronizzazione per SQL Server  
  
##### <a name="default-action-on-local-and-remote-object-change"></a>Azione predefinita in locale e remoto Modifica oggetto  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando la definizione dell'oggetto cambia in SSMA e nel server di database.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **scrivere nel Database**, SSMA aggiornerà gli oggetti del database in base al contenuto dei metadati SSMA quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  
##### <a name="default-action-on-local-object-change"></a>Operazione predefinita sulla modifica di un oggetto locale  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando l'oggetto viene modificato in SSMA.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **scrivere nel Database**, SSMA aggiornerà l'oggetto nel database in base al contenuto dei metadati SSMA quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  
##### <a name="default-action-on-remote-object-change"></a>Operazione predefinita sulla modifica di un oggetto remoto  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando gli oggetti modificati nel server di database.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **scrivere nel Database**, SSMA aggiornerà l'oggetto nel database in base al contenuto dei metadati SSMA quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  
##### <a name="default-action-when-local-object-metadata-is-missing"></a>Azione predefinita quando i metadati dell'oggetto locale sono mancanti  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando mancano i metadati locali.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA consente di selezionare l'aggiornamento dall'opzione di Database quando viene soddisfatta la condizione.  
  
-   Se si seleziona **scrivere nel Database**, SSMA eliminerà l'oggetto dal database quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  

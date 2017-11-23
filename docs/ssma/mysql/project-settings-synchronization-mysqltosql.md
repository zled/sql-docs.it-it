---
title: Impostazioni (sincronizzazione) (MySQLToSQL) del progetto | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 42061ff7-e6e7-497b-a0d9-440b9cf5986c
caps.latest.revision: "3"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 27a5deab2aec74b58e2d23f3812246a15659ff20
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="project-settings-synchronization-mysqltosql"></a>Impostazioni del progetto (sincronizzazione) (MySQLToSQL)
La sincronizzazione **le impostazioni del progetto** consentono di configurare la modalità di sincronizzazione degli oggetti di database MySQL con gli oggetti di database di SQL Server.  
  
Le azioni predefinite specificano le impostazioni predefinite per l'aggiornamento di oggetti dal database di MySQL e per la sincronizzazione degli oggetti con il database di SQL Server. Per ulteriori informazioni, vedere [Aggiorna da database &#40; MySQLToSQL &#41;](../../ssma/mysql/refresh-from-database-mysqltosql.md)  
  
È possibile accedere a due diverse pagine di sincronizzazione che contengono le stesse impostazioni:  
  
-   Per specificare impostazioni per tutti i progetti futuri di SSMA, il **strumenti** menu, fare clic su **DefaultProject impostazioni**e quindi fare clic su **sincronizzazione** nella parte inferiore del riquadro a sinistra.  
  
-   Per specificare le impostazioni per il progetto corrente, il **strumenti** menu, fare clic su **impostazioni progetto**e quindi fare clic su **sincronizzazione** nella parte inferiore del riquadro a sinistra.  
  
## <a name="options"></a>Opzioni  
  
##### <a name="misc"></a>Varie  
  
##### <a name="attempts"></a>Tentativi  
Fornisce le informazioni sul numero di passaggi di rendere gli oggetti da caricare in SQL Server. Caricamento degli oggetti in SQL Server viene in genere eseguito in più passaggi. Gli oggetti che non riescono a caricare il primo passaggio, ad esempio le chiavi esterne, potrebbero caricare correttamente il passaggio successivo.  
  
Per impostazione predefinita il valore è 2.  
  
## <a name="synchronization-for-mysql"></a>Sincronizzazione per MySQL  
  
##### <a name="action-on-local-and-remote-object-change"></a>Azione di modifica di oggetti locali e remoti  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando la definizione dell'oggetto cambia in SSMA e nel server di database.  
  
-   Se si seleziona l'aggiornamento dal Database, SSMA caricare le definizioni di database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona Ignora, SSMA non eseguirà alcuna azione di aggiornamento.  
  
##### <a name="action-on-local-object-change"></a>Azione di modifica di un oggetto locale  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando l'oggetto viene modificato in SSMA.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  
##### <a name="action-on-remote-object-change"></a>Azione di modifica di un oggetto remoto  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando gli oggetti modificati nel server di database.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  
##### <a name="action-when-local-object-metadata-is-missing"></a>Azione quando i metadati dell'oggetto locale sono mancanti  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando i metadati locali sono mancanti.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento  
  
## <a name="synchronization-for-sql-server"></a>Sincronizzazione per SQL Server  
  
##### <a name="action-on-local-and-remote-object-change"></a>Azione in locale e remoto Modifica oggetto  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando la definizione dell'oggetto cambia in SSMA e nel server di database.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **scrivere nel Database**, SSMA aggiornerà gli oggetti del database in base al contenuto dei metadati SSMA quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  
##### <a name="action-on-local-object-change"></a>Azione di modifica di un oggetto locale  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando l'oggetto viene modificato in SSMA.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **scrivere nel Database**, SSMA aggiornerà l'oggetto nel database in base al contenuto dei metadati SSMA quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  
##### <a name="action-on-remote-object-change"></a>Azione di modifica di un oggetto remoto  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando gli oggetti modificati nel server di database.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA caricherà le definizioni di database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **scrivere nel Database**, SSMA aggiornerà l'oggetto nel database in base al contenuto dei metadati SSMA quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  
##### <a name="action-when-local-object-metadata-is-missing"></a>Azione quando i metadati dell'oggetto locale sono mancanti  
Specifica l'impostazione predefinita nella finestra di dialogo sincronizzazione quando mancano i metadati locali.  
  
-   Se si seleziona **aggiornamento dal Database**, SSMA consente di selezionare l'aggiornamento dall'opzione di Database quando viene soddisfatta la condizione.  
  
-   Se si seleziona **scrivere nel Database**, SSMA eliminerà l'oggetto dal database quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Skip**, SSMA non verrà eseguita un'azione di aggiornamento.  
  

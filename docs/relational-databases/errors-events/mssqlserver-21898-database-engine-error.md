---
title: MSSQLSERVER_21898 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 21898 (Database Engine error)
ms.assetid: 02405b21-3d4e-4c2d-b4b3-d7b1ec05edb4
caps.latest.revision: 6
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2ef113042671707c655a47b95d372c3c16dcc1c1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver21898"></a>MSSQLSERVER_21898
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|21898|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SQLErrorNum21898|  
|Testo del messaggio|Il server di pubblicazione '%s' utilizza il database di distribuzione '%s' e non '%s' che è richiesto per ospitare il database di pubblicazione '%s.' Eseguire **sp_changedistpublisher** sul database di distribuzione '%s' per modificare il database di distribuzione usato dal server di pubblicazione in '%s'.|  
  
## <a name="explanation"></a>Spiegazione  
**sp_validate_redirected_publisher** esegue una query di msdb.dbo.MSdistpublishers nel database di distribuzione locale per verificare che il database di distribuzione usato dal nuovo server di pubblicazione sia uguale a quello usato dal server di pubblicazione originale. Questo errore viene restituito quando questi database sono diversi, rendendo il server di pubblicazione un host non adatto al database del server di pubblicazione.  
  
## <a name="user-action"></a>Azione dell'utente  
Eseguire la stored procedure **sp_changedistpublisher** per modificare il database di distribuzione per il nuovo server di pubblicazione usato dal server di pubblicazione originale.  
  
> [!NOTE]  
> Con l'esecuzione di **sp_changedistpublisher** il problema verrà indirizzato se è stato immesso il database di distribuzione errato durante l'esecuzione di **sp_adddistpublisher** sul database di distribuzione per il server di pubblicazione. Tuttavia, se il server di pubblicazione remoto dispone di pubblicazioni esistenti di un altro database di pubblicazione che utilizza il database di distribuzione identificato, questa modifica non è adatta. La replica con il database di distribuzione denominato deve essere rimossa sistematicamente e quindi ristabilita utilizzando il database di distribuzione del server di pubblicazione originale affinché il nuovo server di pubblicazione funzioni come un host adatto.  
  

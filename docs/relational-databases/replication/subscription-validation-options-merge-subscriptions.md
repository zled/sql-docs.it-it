---
title: Opzioni di convalida delle sottoscrizioni (sottoscrizioni di tipo merge) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.validate.mergeoptions.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: 4958c4ab-2025-42ce-b836-6fb4e9e6f24d
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c966b258a333b53a8e14686ccb32228655ce7b3a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47650109"
---
# <a name="subscription-validation-options-merge-subscriptions"></a>Opzioni di convalida delle sottoscrizioni (sottoscrizioni di tipo merge)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Utilizzare la finestra di dialogo **Opzioni di convalida delle sottoscrizioni** per specificare se la convalida deve utilizzare solo il conteggio delle righe o deve utilizzare il conteggio delle righe e il checksum binario.  
  
## <a name="options"></a>Opzioni  
 **Verifica solo il conteggio delle righe**  
 Consente di verificare che la tabella nel Sottoscrittore abbia lo stesso numero di righe della tabella nel server di pubblicazione. Questa opzione non convalida la corrispondenza del contenuto delle righe. La convalida del conteggio delle righe è un controllo non approfondito che consente comunque di evidenziare eventuali problemi dei dati.  
  
 **Verifica il conteggio delle righe e confronta i valori di checksum per la verifica dei dati delle righe**  
 Oltre al conteggio delle righe nel server di pubblicazione e nel Sottoscrittore, viene calcolato un checksum di tutti i dati utilizzando l'algoritmo di checksum binario. In caso di esito negativo durante il conteggio delle righe il checksum non viene eseguito. Questa opzione non è valida per [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Convalidare i dati nel Sottoscrittore](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [Convalidare i dati replicati](../../relational-databases/replication/validate-replicated-data.md)  
  
  

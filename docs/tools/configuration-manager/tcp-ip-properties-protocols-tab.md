---
title: "Proprietà TCP/IP (scheda protocolli) | Documenti Microsoft"
ms.custom: 
ms.date: 08/24/2016
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TCP/IP [SQL Server], configuration options
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
caps.latest.revision: "38"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eacd9f77d0794038ce3d4df00f4af06d8e232e6e
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="tcpip-properties-protocols-tab"></a>Proprietà TCP/IP (scheda Protocolli)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Utilizzare il **proprietà TCP/IP** la finestra di dialogo per configurare le opzioni per il protocollo TCP/IP. Fare clic su **TCP/IP** nel riquadro sinistro per visualizzare le configurazioni dei singoli indirizzi IP nel riquadro dei dettagli.  
  
 Per rendere effettive le modifiche, è necessario riavviare Microsoft SQL Server.  
  
## <a name="options"></a>Opzioni  
 **Abilitata**  
 I valori possibili sono **Sì** e **No**.  
  
 **Keep-alive**  
 Specificare l'intervallo, in millisecondi, in cui i pacchetti keep-alive vengono trasmessi per verificare che il computer remoto sia ancora disponibile.  
  
 **Attesa su tutti**  
 Specificare se SQL Server resterà in attesa su tutti gli indirizzi IP associati alle schede di rete del computer. Se è impostato su **No**, configurare separatamente ogni indirizzo IP usando la finestra di dialogo delle proprietà dei singoli indirizzi. Se è impostato su **Sì**, le impostazioni della casella delle proprietà relative a **IPAll** verranno applicate a tutti gli indirizzi IP. Il valore predefinito è **Sì**.  
  
 **Nessun ritardo**  
 SQL Server non implementa modifiche in questa proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Scelta di un protocollo di rete](https://msdn.microsoft.com/library/ms187892(v=sql.130).aspx)   
 [Creazione di una stringa di connessione valida con TCP/IP](creating-a-valid-connection-string-using-tcp-ip.md)  
  
  

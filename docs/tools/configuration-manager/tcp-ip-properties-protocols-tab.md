---
title: "Propriet&#224; TCP/IP (scheda Protocolli) | Microsoft Docs"
ms.custom: ""
ms.date: "08/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TCP/IP [SQL Server], opzioni di configurazione"
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Propriet&#224; TCP/IP (scheda Protocolli)
  La finestra di dialogo **Proprietà - TCP/IP** consente di configurare le opzioni relative al protocollo TCP/IP. Fare clic su **TCP/IP** nel riquadro sinistro per visualizzare le configurazioni dei singoli indirizzi IP nel riquadro dei dettagli.  
  
 Per rendere effettive le modifiche, è necessario riavviare Microsoft SQL Server.  
  
## Opzioni  
 **Abilitata**  
 I valori possibili sono **Sì** e **No**.  
  
 **Keep-alive**  
 Specificare l'intervallo, in millisecondi, in cui i pacchetti keep-alive vengono trasmessi per verificare che il computer remoto sia ancora disponibile.  
  
 **Attesa su tutti**  
 Specificare se SQL Server resterà in attesa su tutti gli indirizzi IP associati alle schede di rete del computer. Se è impostato su **No**, configurare separatamente ogni indirizzo IP usando la finestra di dialogo delle proprietà dei singoli indirizzi. Se è impostato su **Sì**, le impostazioni della casella delle proprietà relative a **IPAll** verranno applicate a tutti gli indirizzi IP. Il valore predefinito è **Sì**.  
  
 **Nessun ritardo**  
 SQL Server non implementa modifiche in questa proprietà.  
  
## Vedere anche  
 [Scelta di un protocollo di rete](https://msdn.microsoft.com/library/ms187892(v=sql.130).aspx)   
 [Creazione di una stringa di connessione valida con TCP/IP](https://msdn.microsoft.com/library/ms191260.aspx)  
  
  
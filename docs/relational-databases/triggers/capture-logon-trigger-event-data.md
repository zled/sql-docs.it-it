---
title: Acquisire i dati degli eventi per i trigger di accesso | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e05b1ab4-c10b-402a-9591-f6ec1e3db8c0
caps.latest.revision: "5"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fb92fa8835369025c8f56eeea32e8d1770dcb673
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="capture-logon-trigger-event-data"></a>Acquisizione dei dati degli eventi per i trigger di accesso
  Per acquisire dati XML per gli eventi LOGON da utilizzare in trigger LOGON, è possibile utilizzare la funzione [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md) . L'evento LOGON restituisce lo schema di dati di evento seguente:  
  
 `<EVENT_INSTANCE>`  
  
 `<EventType>event_type</EventType>`  
  
 `<PostTime>post_time</PostTime>`  
  
 `<SPID>spid</SPID>`  
  
 `<ServerName>server_name</ServerName>`  
  
 `<LoginName>login_name</LoginName>`  
  
 `<LoginType>login_type</LoginType>`  
  
 `<SID>sid</SID>`  
  
 `<ClientHost>client_host</ClientHost>`  
  
 `<IsPooled>is_pooled</IsPooled>`  
  
 `</EVENT_INSTANCE>`  
  
 `<EventType>`  
 Contiene `LOGON`.  
  
 `<PostTime>`  
 Contiene l'ora in cui viene richiesta l'attivazione di una sessione.  
  
 `<SID>`  
 Contiene il flusso binario codificato in base 64 dell'ID di sicurezza (SID) per il nome di account di accesso specificato.  
  
 `<ClientHost>`  
 Contiene il nome host del client da cui viene attivata la connessione. Il valore è '`<local_machine>`' se il nome del client e del server coincidono. In caso contrario, il valore corrisponde all'indirizzo IP del client.  
  
 `<IsPooled>`  
 Il valore è `1` se la connessione viene riutilizzata tramite pool di connessioni. In caso contrario, il valore è `0`.  
  
  

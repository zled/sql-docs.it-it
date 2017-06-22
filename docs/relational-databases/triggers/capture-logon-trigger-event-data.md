---
title: Acquisire i dati degli eventi per i trigger di accesso | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e05b1ab4-c10b-402a-9591-f6ec1e3db8c0
caps.latest.revision: 5
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 790a086c90eeeeb606a86056f239853d805cb091
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

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
  
  

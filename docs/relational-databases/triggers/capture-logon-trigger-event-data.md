---
title: Acquisire i dati degli eventi per i trigger di accesso | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: triggers
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e05b1ab4-c10b-402a-9591-f6ec1e3db8c0
caps.latest.revision: "5"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f416a2ce4e59d9d097348fb601825867df10d7b4
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="capture-logon-trigger-event-data"></a>Acquisizione dei dati degli eventi per i trigger di accesso
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)] Per acquisire dati XML sugli eventi LOGON da usare in trigger LOGON, è possibile usare la funzione [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md). L'evento LOGON restituisce lo schema di dati di evento seguente:  
  
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
  
  

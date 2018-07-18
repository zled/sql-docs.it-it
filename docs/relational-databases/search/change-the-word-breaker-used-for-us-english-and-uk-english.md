---
title: Modificare il word breaker usato per le lingue Inglese (Stati Uniti) e Inglese (Regno Unito) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.component: search
ms.reviewer: ''
ms.suite: sql
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6b5d2177-db98-47f5-b32e-4b80a2f74ffe
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 2213afdfdb67449e96363e5ea9e5009a93ba9132
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="change-the-word-breaker-used-for-us-english-and-uk-english"></a>Modifica del word breaker utilizzato per le lingue Inglese (Stati Uniti) e Inglese (Regno Unito)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installa una nuova versione (versione 14.0.4999.1038) del word breaker e dello stemmer per la lingua inglese che sostituisce la versione precedente (versione 12.0.6828.0). Per informazioni sul comportamento modificato dei nuovi componenti, vedere [Differenze di comportamento nella ricerca full-text](http://msdn.microsoft.com/library/573444e8-51bc-4f3d-9813-0037d2e13b8f). In questo argomento viene descritto come passare dalla nuova versione di questi componenti alla versione precedente o come tornare alla nuova versione dalla versione precedente. Per le installazioni di cluster, queste modifiche devono essere apportate in tutti i nodi primari e passivi.  
  
 Le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzano word breaker diversi rappresentati da CLSID diversi per la lingua inglese Stati Uniti (LCID 1033) e per la lingua inglese Regno Unito (LCID 2057). In questa versione entrambi gli LCID utilizzano gli stessi componenti con gli stessi CLSID, come illustrato nella tabella seguente:  
  
|LCID|Word breaker installato tramite le versioni precedenti<br /><br /> Versione 12.0.6828.0|Stemmer installato tramite le versioni precedenti|Word breaker installato tramite questa versione<br /><br /> Versione 14.0.4999.1038|Stemmer installato tramite questa versione|  
|----------|-------------------------------------------------------------------------|--------------------------------------------|-----------------------------------------------------------------------|---------------------------------------|  
|1033<br />(inglese Stati Uniti)|188D6CC5-CB03-4C01-912E-47D21295D77E|EEED4C20-7F1B-11CE-BE57-00AA0051FE20|9faed859-0b30-4434-ae65-412e14a16fb8|e1e5ef84-c4a6-4e50-8188-99aef3de2659|  
|2057<br />(inglese Regno Unito)|173C97E2-AEBE-437C-9445-01B237ABF2F6|D99F7670-7F1A-11CE-BE57-00AA0051FE20|9faed859-0b30-4434-ae65-412e14a16fb8|e1e5ef84-c4a6-4e50-8188-99aef3de2659|  
  
 I componenti descritti in questo argomento sono file DLL installati nella cartella `MSSQL\Binn` per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Il percorso completo è in genere `C:\Program Files\Microsoft SQL Server\<instance>\MSSQL\Binn`.  
  
 Per informazioni generali su word breaker e stemmer, vedere [Configurare e gestire word breaker e stemmer per la ricerca](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md).  
  
## <a name="switching-from-the-current-english-word-breaker-to-the-previous-english-word-breakers"></a>Passaggio dal word breaker per la lingua inglese corrente ai word breaker per la lingua inglese precedenti  
  
#### <a name="to-switch-from-the-current-version-of-the-us-english-word-breaker-to-the-previous-version"></a>Per passare dalla versione corrente del word breaker per la lingua inglese Stati Uniti alla versione precedente  
  
1.  Nel Registro di sistema spostarsi sul nodo seguente: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<RadiceIstanza\>\MSSearch\CLSID**.  
  
2.  Utilizzare i passaggi seguenti per aggiungere nuove chiavi per i ClassID COM per le interfacce del word breaker e dello stemmer per la lingua inglese Stati Uniti precedenti per l'LCID 1033:  
  
    1.  Aggiungere una nuova chiave con il valore **{188D6CC5-CB03-4C01-912E-47D21295D77E}** per il word breaker precedente.  
  
    2.  Aggiornare i dati (predefiniti) del valore della chiave a **langwrbk.dll**.  
  
    3.  Aggiungere una nuova chiave con il valore **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}** per lo stemmer precedente.  
  
    4.  Aggiornare i dati (predefiniti) del valore della chiave a **infosoft.dll**.  
  
3.  Nel Registro di sistema spostarsi sul nodo seguente: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<RadiceIstanza\>\MSSearch\Language\enu**.  
  
4.  Aggiornare il valore della chiave **WBreakerClass** a **{188D6CC5-CB03-4C01-912E-47D21295D77E}**.  
  
5.  Aggiornare il valore della chiave **StemmerClass** a **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}**.  
  
6.  Riavviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
#### <a name="to-switch-from-the-current-version-of-the-uk-english-word-breaker-to-the-previous-version"></a>Per passare dalla versione corrente del word breaker per la lingua inglese Regno Unito alla versione precedente  
  
1.  Nel Registro di sistema spostarsi sul nodo seguente: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<RadiceIstanza\>\MSSearch\CLSID**.  
  
2.  Utilizzare i passaggi seguenti per aggiungere una nuova chiave per i ClassID COM per le interfacce del word breaker e dello stemmer per la lingua inglese Regno Unito precedenti per l'LCID 2057:  
  
    1.  Aggiungere una nuova chiave con il valore **{173C97E2-AEBE-437C-9445-01B237ABF2F6}** per il word breaker precedente.  
  
    2.  Aggiornare i dati (predefiniti) del valore della chiave a **langwrbk.dll**.  
  
    3.  Aggiungere una nuova chiave con il valore **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}** per lo stemmer precedente.  
  
    4.  Aggiornare i dati (predefiniti) del valore della chiave a **infosoft.dll**.  
  
3.  Nel Registro di sistema passare al nodo seguente: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<RadiceIstanza\>\MSSearch\Language\eng**.  
  
4.  Aggiornare il valore della chiave **WBreakerClass** a **{173C97E2-AEBE-437C-9445-01B237ABF2F6}**.  
  
5.  Aggiornare il valore della chiave **StemmerClass** a **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}**.  
  
6.  Riavviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="switching-back-from-the-previous-english-word-breakers-to-the-current-english-word-breaker"></a>Passaggio dai word breaker per la lingua inglese precedenti al word breaker per la lingua inglese corrente  
  
#### <a name="to-switch-back-from-the-previous-version-of-the-us-english-word-breaker-to-the-current-version"></a>Per tornare alla versione corrente del word breaker per la lingua inglese Stati Uniti dalla versione precedente  
  
1.  Nel Registro di sistema spostarsi sul nodo seguente: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<RadiceIstanza\>\MSSearch\CLSID**.  
  
2.  Se le chiavi seguenti non sono presenti, utilizzare la procedura indicata di seguito per aggiungere una nuova chiave per i ClassID COM per le interfacce del word breaker e dello stemmer per la lingua inglese Stati Uniti correnti per l'LCID 1033:  
  
    1.  Aggiungere una nuova chiave con il valore **{9faed859-0b30-4434-ae65-412e14a16fb8}** per il word breaker corrente.  
  
    2.  Aggiornare i dati (predefiniti) del valore della chiave a **MsWb7.dll**.  
  
    3.  Aggiungere una nuova chiave con il valore **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** per lo stemmer corrente.  
  
    4.  Aggiornare i dati (predefiniti) del valore della chiave a **MsWb7.dll**.  
  
3.  Nel Registro di sistema passare al nodo seguente: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<RadiceIstanza\>\MSSearch\Language\eng**.  
  
4.  Aggiornare il valore della chiave **WBreakerClass** a **{9faed859-0b30-4434-ae65-412e14a16fb8}**.  
  
5.  Aggiornare il valore della chiave **StemmerClass** a **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}**.  
  
6.  Riavviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
#### <a name="to-switch-back-from-the-previous-version-of-the-uk-english-word-breaker-to-the-current-version"></a>Per tornare alla versione corrente del word breaker per la lingua inglese Regno Unito dalla versione precedente  
  
1.  Nel Registro di sistema spostarsi sul nodo seguente: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<RadiceIstanza\>\MSSearch\CLSID**.  
  
2.  Se le chiavi seguenti non sono presenti, utilizzare la procedura indicata di seguito per aggiungere una nuova chiave per i ClassID COM per le interfacce del word breaker e dello stemmer per la lingua inglese Regno Unito correnti per l'LCID 2057:  
  
    1.  Aggiungere una nuova chiave con il valore **{9faed859-0b30-4434-ae65-412e14a16fb8}** per il word breaker corrente.  
  
    2.  Aggiornare i dati (predefiniti) del valore della chiave a **MsWb7.dll**.  
  
    3.  Aggiungere una nuova chiave con il valore **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** per lo stemmer corrente.  
  
    4.  Aggiornare i dati (predefiniti) del valore della chiave a **MsWb7.dll**.  
  
3.  Nel Registro di sistema passare al nodo seguente: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<RadiceIstanza\>\MSSearch\Language\eng**.  
  
4.  Aggiornare il valore della chiave **WBreakerClass** a **{9faed859-0b30-4434-ae65-412e14a16fb8}**.  
  
5.  Aggiornare il valore della chiave **StemmerClass** a **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}**.  
  
6.  Riavviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Ripristinare i word breaker utilizzati dalla ricerca alla versione precedente](../../relational-databases/search/revert-the-word-breakers-used-by-search-to-the-previous-version.md)   
 [Differenze di comportamento nella ricerca full-text](http://msdn.microsoft.com/library/573444e8-51bc-4f3d-9813-0037d2e13b8f)  
  
  

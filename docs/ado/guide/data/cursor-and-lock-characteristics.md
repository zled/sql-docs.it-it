---
title: Cursore e le caratteristiche di blocco | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- locks [ADO], characteristics
- adOpenDynamic [ADO]
- cursors [ADO], characteristics
ms.assetid: 459c29cb-4230-42bf-8cc2-f3132ccc7aba
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e843192c1ad00c9e7ef6742938d7dfe3dcc1bd07
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="cursor-and-lock-characteristics"></a>Cursore e le caratteristiche di blocco
Mentre le caratteristiche di un cursore dipendono dalle funzionalità del provider, i vantaggi e gli svantaggi seguenti si applicano in genere per i vari tipi di cursori e blocchi.  
  
|Tipo di cursore o di blocco|Vantaggi|Svantaggi|  
|-------------------------|----------------|-------------------|  
|**adOpenForwardOnly**|-Requisiti di risorse basso|-Non è possibile scorrere indietro<br />-Nessuna concorrenza dei dati|  
|**adOpenStatic**|-Scorrevole|-Nessuna concorrenza dei dati|  
|**adOpenKeyset**|La concorrenza alcuni dei dati<br />-Scorrevole|-Requisiti di risorse superiori<br />-Non è disponibile in uno scenario disconnesso|  
|**adOpenDynamic**|-Concorrenza dei dati alto<br />-Scorrevole|-Requisiti di risorse massimo<br />-Non è disponibile in uno scenario disconnesso|  
|**adLockReadOnly**|-Requisiti di risorse basso<br />-Altamente scalabile|-Data non è aggiornabile tramite cursore|  
|**adLockBatchOptimistic**|-Gli aggiornamenti batch<br />-Scenari disconnessi<br />-Gli altri utenti di accedere ai dati|-Dati possono essere modificati contemporaneamente da più utenti|  
|**adLockPessimistic**|-Data non può essere modificato da altri utenti durante il blocco|-Impedisce ad altri utenti di accedere ai dati durante il blocco|  
|**adLockOptimistic**|-Gli altri utenti di accedere ai dati|-Dati possono essere modificati contemporaneamente da più utenti|

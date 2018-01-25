---
title: Verificare i problemi correlati ai tentativi di lettura nel sottosistema di I/O del disco | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: cedf4097-5b73-4964-9935-74a101847019
caps.latest.revision: "8"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e5c90473fa372a3bc04433c6f093cb8997f6ee9e
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="check-disk-input-output-subsystem-for-read-retry-problems"></a>Verifica dei problemi correlati ai tentativi di lettura nel sottosistema di input/output del disco
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Questa regola verifica la presenza del messaggio di errore 825 di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel registro eventi. Tale messaggio indica che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è stato in grado per di leggere dati dal disco al primo tentativo. Il messaggio indica un problema grave relativo al sottosistema di I/O del disco Questo messaggio non indica attualmente un problema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Se non viene risolto, tuttavia, il problema del disco potrebbe provocare la perdita di dati o il danneggiamento del database.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Le azioni seguenti possono contribuire a individuare e risolvere il problema hardware sottostante:  
  
-   Esaminare il log degli errori e il testo delle variabili di questo messaggio per individuare eventuali indizi che consentano di spiegare il problema.  
  
-   Controllare il sistema di dischi. Il problema potrebbe essere correlato ai dischi, ai controller dei dischi, alle schede di array o ai driver dei dischi.  
  
-   Contattare il produttore dei dischi e richiedere le utilità più recenti per verificare lo stato del sistema di dischi.  
  
-   Contattare il produttore dei dischi e richiedere gli ultimi aggiornamenti dei driver.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [MSSQLSERVER_825](http://msdn.microsoft.com/library/f69f8214-5af1-4769-878b-117ad6eaff52)  
  
 [SQL Server I/O Basics, Chapter 2](http://go.microsoft.com/fwlink/?linkid=69370)  
  
  

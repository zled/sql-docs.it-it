---
title: MSSQLSERVER_50000 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: reference
helpviewer_keywords:
- 50000 [SQL Server Native Client setup error]
ms.assetid: 5426d87a-d5d9-4984-b211-b07d69e834a2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 741420467a50aff6cdd0486c91dbf69224b160e7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48223411"
---
# <a name="mssqlserver50000"></a>MSSQLSERVER_50000
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|Versione prodotto|11.0|  
|ID evento|50000|  
|Origine evento|SETUP|  
|Componente|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client|  
|Nome simbolico||  
|Testo del messaggio|Errore di rete durante il tentativo di lettura dal file '%. * ls.'|  
  
## <a name="explanation"></a>Spiegazione  
 È stato eseguito il tentativo di installare (o aggiornare) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client in un computer in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client è già stato installato da un file MSI che è stato rinominato da sqlncli.msi.  
  
## <a name="user-action"></a>Azione dell'utente  
 Per risolvere il problema, disinstallare la versione esistente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Per prevenire questo errore, non installare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client da un file MSI non denominato sqlncli.msi.  
  
## <a name="internal-only"></a>Solo interno  
  

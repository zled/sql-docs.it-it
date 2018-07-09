---
title: MSSQLSERVER_50000 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.component: native-client
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- 50000 [SQL Server Native Client setup error]
ms.assetid: 5426d87a-d5d9-4984-b211-b07d69e834a2
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2244b3a1b72263489a67b6ce4c6d23d44deb6bca
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428410"
---
# <a name="sql-server-native-client-error-mssqlserver50000"></a>Errore di SQL Server Native Client MSSQLSERVER_50000
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

    
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
  

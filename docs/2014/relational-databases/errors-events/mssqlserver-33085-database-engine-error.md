---
title: MSSQLSERVER_33085 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 33085 (Database Engine error)
ms.assetid: c27b8d1d-668a-4ba8-8b61-25a5ebbc5485
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fa7b45227050af057a5e5005a6664c973855b040
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421030"
---
# <a name="mssqlserver33085"></a>MSSQLSERVER_33085
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|33085|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SEC_CRYPTOPROVE_METHOD_CANNOT_FOUND|  
|Testo del messaggio|Impossibile trovare uno o più metodi nella libreria del provider del servizio di crittografia '%.* ls.'|  
  
## <a name="explanation"></a>Spiegazione  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è stato in grado di usare il provider del servizio di crittografia elencato nel messaggio di errore. Il provider del servizio di crittografia non supporta un metodo obbligatorio. Lo stato dell'errore indica il metodo non trovato.  
  
|State|Description|  
|-----------|-----------------|  
|1|SqlCryptInitializeProvider|  
|2|SqlCryptFreeProvider|  
|3|SqlCryptOpenSession|  
|4|SqlCryptCloseSession|  
|5|SqlCryptGetProviderInfo|  
|6|SqlCryptGetNextAlgorithmId|  
|7|SqlCryptGetAlgorithmInfo|  
|8|SqlCryptCreateKey|  
|9|SqlCryptDropKey|  
|10|SqlCryptGetNextKeyId|  
|11|SqlCryptGetKeyInfoByKeyId|  
|12|SqlCryptGetKeyInfoByThumb|  
|13|SqlCryptGetKeyInfoByName|  
|14|SqlCryptExportKey|  
|15|SqlCryptImportKey|  
|16|SqlCryptEncrypt|  
|17|SqlCryptDecrypt|  
  
## <a name="user-action"></a>Azione dell'utente  
 Per ulteriori informazioni, contattare il provider del servizio di crittografia.  
  
  

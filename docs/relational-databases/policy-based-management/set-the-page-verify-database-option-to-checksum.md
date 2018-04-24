---
title: Impostare l'opzione di database PAGE_VERIFY su CHECKSUM | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 686b9a4a-ea61-4263-9ab8-f444a3077679
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 696d31fbc8c9bf0fd218070228f50311643ec2f9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="set-the-pageverify-database-option-to-checksum"></a>Impostazione dell'opzione di database PAGE_VERIFY su CHECKSUM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Questa regola consente di controllare se l'opzione di database PAGE_VERIFY è impostata su CHECKSUM. Se per l'opzione di database PAGE_VERIFY si specifica CHECKSUM, il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] calcola un checksum sul contenuto dell'intera pagina e archivia il valore nell'intestazione di pagina quando viene scritta una pagina nel disco. Quando si esegue la lettura della pagina dal disco, il checksum viene ricalcolato e confrontato con il valore di checksum archiviato nell'intestazione della pagina. In questo modo viene garantito un livello elevato di integrità dei file di dati.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Impostare l'opzione di database PAGE_VERIFY su CHECKSUM.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Opzioni di ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
  

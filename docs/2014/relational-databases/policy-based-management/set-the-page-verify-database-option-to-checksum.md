---
title: Impostare l'opzione di database PAGE_VERIFY su CHECKSUM | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 686b9a4a-ea61-4263-9ab8-f444a3077679
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9d2b40d798eb06a294b6703a17b5f0da31c59131
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48201978"
---
# <a name="set-the-pageverify-database-option-to-checksum"></a>Impostazione dell'opzione di database PAGE_VERIFY su CHECKSUM
  Questa regola consente di controllare se l'opzione di database PAGE_VERIFY è impostata su CHECKSUM. Se per l'opzione di database PAGE_VERIFY si specifica CHECKSUM, il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] calcola un checksum sul contenuto dell'intera pagina e archivia il valore nell'intestazione di pagina quando viene scritta una pagina nel disco. Quando si esegue la lettura della pagina dal disco, il checksum viene ricalcolato e confrontato con il valore di checksum archiviato nell'intestazione della pagina. In questo modo viene garantito un livello elevato di integrità dei file di dati.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Impostare l'opzione di database PAGE_VERIFY su CHECKSUM.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Opzioni di ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
  

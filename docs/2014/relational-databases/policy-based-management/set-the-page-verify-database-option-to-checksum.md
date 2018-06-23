---
title: Impostare l'opzione di database PAGE_VERIFY su CHECKSUM | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 686b9a4a-ea61-4263-9ab8-f444a3077679
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fb7e0f5db0052b4eaac527a81a7825be2da16df0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067160"
---
# <a name="set-the-pageverify-database-option-to-checksum"></a>Impostazione dell'opzione di database PAGE_VERIFY su CHECKSUM
  Questa regola consente di controllare se l'opzione di database PAGE_VERIFY è impostata su CHECKSUM. Se per l'opzione di database PAGE_VERIFY si specifica CHECKSUM, il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] calcola un checksum sul contenuto dell'intera pagina e archivia il valore nell'intestazione di pagina quando viene scritta una pagina nel disco. Quando si esegue la lettura della pagina dal disco, il checksum viene ricalcolato e confrontato con il valore di checksum archiviato nell'intestazione della pagina. In questo modo viene garantito un livello elevato di integrità dei file di dati.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Impostare l'opzione di database PAGE_VERIFY su CHECKSUM.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Opzioni di ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
  

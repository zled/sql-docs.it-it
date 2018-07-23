---
title: 'Procedura: Eseguire una query parziale | Microsoft Docs'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: af04ab37-6cbb-4185-9382-e5922fa5b1df
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1c6ed1362f7001a55b74538c165b373364b93df3
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087473"
---
# <a name="how-to-execute-a-partial-query"></a>Procedura: Esecuzione di una query parziale
L'Editor Transact\-SQL consente di evidenziare un segmento specifico dello script ed eseguirlo come una singola query. In questo modo è più semplice eseguire il debug di sezioni di query complesse.  
  
> [!WARNING]  
> Nella procedura seguente vengono usate entità create nelle procedure precedenti nelle sezioni [Sviluppo del database connesso](../ssdt/connected-database-development.md) e [Sviluppo di database offline orientato ai progetti](../ssdt/project-oriented-offline-database-development.md).  
  
### <a name="to-partially-execute-a-query"></a>Per eseguire parzialmente una query  
  
1.  In **Esplora oggetti di SQL Server** fare doppio clic su **PerishableFruits** in **Viste** per aprirlo nell'Editor Transact\-SQL.  
  
2.  Evidenziare il segmento `SELECT p.Id, p.Name FROM dbo.Product p` nel codice, fare clic con il pulsante destro del mouse e scegliere **Esegui query**.  
  
3.  Si noti che tutte le righe con i campi specificati nella tabella `Products` vengono restituite nel riquadro dei**risultati**.  
  

---
title: ICommandWithParameters | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 66644c70-def7-46d8-8c47-b883292a0288
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8c43b41faa03ae9838cc0dcec619179d272f238e
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408151"
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
  Miglioramenti all'inizio del motore di database con [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] consentire ICommandWithParameters:: GetParameterInfo ottenere descrizioni più accurate dei risultati previsti. Questi risultati più accurati differiscano dai valori restituiti da CommandWithParameters::GetParameterInfo nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [individuazione dei metadati](../native-client/features/metadata-discovery.md).  
  
 Inoltre a partire [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], durante la chiamata di ICommandWithParameters:: SetParameterInfo, il valore passato per il *pwszName* parametro deve essere un identificatore valido. Per altre informazioni, vedere [Identificatori del database](../databases/database-identifiers.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Le interfacce &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  

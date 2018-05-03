---
title: ICommandWithParameters | Documenti Microsoft
description: Interfaccia ICommandWithParameters
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: f1cb8b2f1ec9a897e26e8b41be81f5bb42a19989
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Miglioramenti all'inizio del motore di database con [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] consentire ICommandWithParameters:: GetParameterInfo ottenere descrizioni più accurate dei risultati previsti. Questi risultati più accurati differiscano dai valori restituiti da CommandWithParameters::GetParameterInfo nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per ulteriori informazioni, vedere [Metadata Discovery](../../oledb/features/metadata-discovery.md).  
  
 A partire dalla [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], durante la chiamata di ICommandWithParameters:: SetParameterInfo, il valore passato al *pwszName* parametro deve essere un identificatore valido. Per altre informazioni, vedere [Identificatori del database](../../../relational-databases/databases/database-identifiers.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce & #40; OLE DB & #41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  

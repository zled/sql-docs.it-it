---
title: ICommandWithParameters | Microsoft Docs
description: Interfaccia ICommandWithParameters
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: df2ced0a4a9640224db743636f96f8cfd1b35657
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2018
ms.locfileid: "51033599"
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Miglioramenti all'inizio del motore di database con [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] consentire ICommandWithParameters:: GetParameterInfo ottenere descrizioni più accurate dei risultati previsti. Questi risultati più accurati differiscano dai valori restituiti da CommandWithParameters::GetParameterInfo nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [Metadata Discovery](../../oledb/features/metadata-discovery.md).  
  
 A partire da [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], inoltre, quando si chiama ICommandWithParameters::SetParameterInfo, il valore passato al parametro *pwszName* deve essere un identificatore valido. Per altre informazioni, vedere [Identificatori del database](../../../relational-databases/databases/database-identifiers.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Le interfacce &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  

---
title: Set di righe MDSCHEMA_KPIS | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_KPIS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_KPIS rowset
ms.assetid: 40fb5112-6a90-4455-82b3-8b6322490222
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 77f6dc3fd3f8e9c92fe1d840c9af646269e0effc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48124461"
---
# <a name="mdschemakpis-rowset"></a>Set di righe MDSCHEMA_KPIS
  Descrive gli indicatori di prestazioni chiave (KPI) all'interno di un database.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `MDSCHEMA_KPIS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Database di origine.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Non supportato.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Cubo padre per l'indicatore di prestazioni chiave (KPI).|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`||Gruppo di misure associato per l'indicatore di prestazioni chiave (KPI).<br /><br /> È possibile utilizzare questa colonna per determinare la dimensionalità dell'indicatore di prestazioni chiave (KPI). Se "**\<NULL >**", l'indicatore KPI verrà dimensionato in base a tutti i gruppi di misure.<br /><br /> Il valore predefinito è "**\<NULL >**".|  
|`KPI_NAME`|`DBTYPE_WSTR`||Nome dell'indicatore di prestazioni chiave (KPI).|  
|`KPI_CAPTION`|`DBTYPE_WSTR`||Etichetta o didascalia associata all'indicatore di prestazioni chiave (KPI). Utilizzata principalmente a scopo di visualizzazione. Se non esiste una didascalia, viene restituito `KPI_NAME`.|  
|`KPI_DESCRIPTION`|`DBTYPE_WSTR`||Descrizione leggibile dell'indicatore di prestazioni chiave (KPI).|  
|`KPI_DISPLAY_FOLDER`|`DBTYPE_WSTR`||Una stringa che identifica il percorso della cartella di visualizzazione che l'applicazione client utilizza per mostrarla al membro. Il separatore di livello delle cartelle è definito dall'applicazione client. Per gli strumenti e i client forniti da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], la barra rovesciata (\\) è il separatore di livello. Per fornire più cartelle di visualizzazione, usare un punto e virgola (;) per separare le cartelle.|  
|`KPI_VALUE`|`DBTYPE_WSTR`||Nome univoco del membro nella dimensione di tipo misura per il valore dell'indicatore di prestazioni chiave (KPI).|  
|`KPI_GOAL`|`DBTYPE_WSTR`||Nome univoco del membro nella dimensione di tipo misura per l'obiettivo dell'indicatore di prestazioni chiave (KPI).<br /><br /> Restituisce `NULL` se non esiste alcun obiettivo definito.|  
|`KPI_STATUS`|`DBTYPE_WSTR`||Nome univoco del membro nella dimensione di tipo misura per lo stato dell'indicatore di prestazioni chiave (KPI).<br /><br /> Restituisce `NULL` se non esiste alcuno stato definito.|  
|`KPI_TREND`|`DBTYPE_WSTR`||Nome univoco del membro nella dimensione di tipo misura per la tendenza dell'indicatore di prestazioni chiave (KPI).<br /><br /> Restituisce `NULL` se non esiste alcuna tendenza definita.|  
|`KPI_STATUS_GRAPHIC`|`DBTYPE_WSTR`||Rappresentazione grafica predefinita dell'indicatore di prestazioni chiave (KPI).|  
|`KPI_TREND_GRAPHIC`|`DBTYPE_WSTR`||Rappresentazione grafica predefinita dell'indicatore di prestazioni chiave (KPI).|  
|`KPI_WEIGHT`|`DBTYPE_WSTR`||Nome univoco del membro nella dimensione di tipo misura per il peso dell'indicatore di prestazioni chiave (KPI).|  
|`KPI_CURRENT_TIME_MEMBER`|`DBTYPE_WSTR`||Nome univoco del membro nella dimensione temporale che definisce il contesto temporale dell'indicatore di prestazioni chiave (KPI).<br /><br /> Restituisce `NULL` se non esiste alcun membro temporale definito.|  
|`KPI_PARENT_KPI_NAME`|`DBTYPE_WSTR`||Nome dell'indicatore di prestazioni chiave (KPI) padre.|  
|`SCOPE`|`DBTYPE_I4`||Ambito dell'indicatore di prestazioni chiave (KPI). L'indicatore di prestazioni chiave (KPI) può corrispondere a un indicatore di prestazioni chiave di sessione o globale.<br /><br /> I possibili valori della colonna sono i seguenti:<br /><br /> -MDKPI_SCOPE_GLOBAL=1 = 1<br />-MDKPI_SCOPE_SESSION=2 = 2|  
|`ANNOTATIONS`|`DBTYPE_WSTR`||(Facoltativo) Set di note, in formato XML.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `MDSCHEMA_KPIS` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`KPI_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Facoltativo) Bitmap con uno dei seguenti valori validi:<br /><br /> -   `1` CUBO<br />-   `2` DIMENSIONE<br /><br /> La restrizione predefinita è impostata su un valore `1`.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  

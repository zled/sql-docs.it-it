---
title: Set di righe DISCOVER_DATASOURCES | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DISCOVER_DATASOURCES
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_DATASOURCES rowset
ms.assetid: f3ff26ab-a447-416b-ba54-1716df2283de
caps.latest.revision: 39
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e319b05d1d9aec74b01b73b671f613a2703d900f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185258"
---
# <a name="discoverdatasources-rowset"></a>Set di righe DISCOVER_DATASOURCES
  Restituisce un elenco delle origini dati del provider XMLA (XML for Analysis) disponibili nel server o servizio Web. Le origini dati pubblicate vengono restituite da un URL del server Web dell'applicazione. Il client può connettersi a una delle origini dati incluse in questo elenco.  
  
 Se si chiama il [Discover](../../xmla/xml-elements-methods-discover.md) metodo con il `DISCOVER_DATASOURCES` il valore di enumerazione nel [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) elemento, il `Discover` metodo restituisce il `DISCOVER_DATASOURCES` set di righe.  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il client seleziona un'origine dati impostando il `DataSourceInfo` proprietà nel [proprietà](../../xmla/xml-elements-properties/properties-element-xmla.md) elemento che viene inviato insieme al [comando](../../xmla/xml-elements-properties/command-element-xmla.md) elemento in base il [Execute](../../xmla/xml-elements-methods-execute.md) metodo. Un client non deve costruire il contenuto della proprietà `DataSourceInfo` da inviare al server. Al contrario, il client deve utilizzare il metodo `Discover` per individuare le origini dati supportate dal provider. Il client restituisce quindi lo stesso valore per la proprietà `DataSourceInfo` ottenuto dal set di righe `DISCOVER_DATASOURCES`.  
  
 Il `DISCOVER_DATASOURCES` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Restrizione|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|`DataSourceName`|`DBTYPE_WSTR`|Sì|Nome dell'origine dati, ad esempio `Adventure Works`.|  
|`DataSourceDescription`|`DBTYPE_WSTR`||Descrizione dell'origine dei dati immessa dal server di pubblicazione.<br /><br /> Potrebbe restituire `NULL`.|  
|`URL`|`DBTYPE_WSTR`|Sì|Percorso univoco che indica la posizione da cui richiamare i metodi XMLA (XML for Analysis) per tale origine dati.<br /><br /> Potrebbe restituire `NULL`.|  
|`DataSourceInfo`|`DBTYPE_WSTR`||Una stringa che contiene eventuali informazioni aggiuntive necessarie per la connessione all'origine dati.<br /><br /> Potrebbe restituire `NULL`.|  
|`ProviderName`|`DBTYPE_WSTR`|Sì|Nome del provider per l'origine dati.<br /><br /> Esempio: `"MSOLAP"`<br /><br /> Potrebbe restituire `NULL`.|  
|`ProviderType`|`DBTYPE_WSTR`|Sì|Tipi di dati supportati dal provider. Questa matrice può includere uno o più dei tipi seguenti:<br /><br /> `MDP`: provider di dati multidimensionali.<br /><br /> `TDP`: provider di dati tabulari.<br /><br /> `DMP`: provider di data mining (implementa la specifica OLE DB per il data mining).|  
|`AuthenticationMode`|`DBTYPE_WSTR`|Sì|Specifica relativa al tipo di modalità di sicurezza utilizzata dall'origine dati. I valori possibili sono i seguenti:<br /><br /> `Unauthenticated`: nessun ID utente o nessuna password da inviare.<br /><br /> `Authenticated`: ID utente e password devono essere inclusi nelle informazioni richieste per connettersi all'origine dati.<br /><br /> `Integrated`: l'origine dati utilizza la sicurezza sottostante per determinare l'autorizzazione, ad esempio la sicurezza integrata fornita da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Internet Information Services (IIS).|  
  
 Questo set di righe dello schema non è ordinato.  
  
> [!IMPORTANT]  
>  Non è possibile eseguire una query sul set di righe `DISCOVER_DATASOURCES` utilizzando query DMV e la sintassi del comando SELECT. È tuttavia possibile eseguire una query sul set di righe `DISCOVER_DATASOURCES` utilizzando <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|valore|  
|--------------|-----------|  
|GUID|06c03d41-f66d-49f3-b1b8-987f7af4cf18|  
|ADOMDNAME|DataSources|  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](xml-for-analysis-schema-rowsets.md)  
  
  

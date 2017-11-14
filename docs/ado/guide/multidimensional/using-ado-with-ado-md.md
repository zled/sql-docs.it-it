---
title: Utilizzo di ADO con ADO MD | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ADO, using with ADO MD
ms.assetid: cfae435e-2ac3-4312-8c1e-9ca4a74cd875
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 38df55c27ced6e0a7b32c321e2b3968bedb73aa1
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="using-ado-with-ado-md"></a>Utilizzo di ADO con ADO MD
ADO e ADO MD sono modelli a oggetti correlato ma separato. ADO fornisce oggetti per la connessione a origini dati, l'esecuzione di comandi, il recupero dei dati e metadati dello schema in un formato tabulare e la visualizzazione di informazioni sugli errori di provider. ADO MD fornisce oggetti per il recupero di dati multidimensionali e visualizzazione dei metadati di schema multidimensionale.  
  
 Quando si lavora con un dati Multidimensionali, è possibile scegliere di utilizzare ADO, ADO MD o entrambi gli elementi con l'applicazione. Facendo riferimento a entrambe le librerie all'interno del progetto, si avrà accesso completo alle funzionalità fornite dai dati Multidimensionali.  
  
 È spesso utile per i consumer ottenere una vista tabulare bidimensionale di un set di dati multidimensionali. È possibile farlo tramite ADO [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto. Specificare l'origine per il [set di celle](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) come il ***origine*** parametro per il [aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md) metodo di un **Recordset**, anziché come origine per un ADO MD **set di celle**.  
  
 Può anche essere utile visualizzare i metadati dello schema in una visualizzazione tabulare anziché come una gerarchia di oggetti. ADO [OpenSchema](../../../ado/reference/ado-api/openschema-method.md) metodo il [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto consente all'utente di aprire un **Recordset** che contiene informazioni sullo schema. Il ***QueryType*** parametro il **OpenSchema** metodo dispone di numerosi [SchemaEnum](../../../ado/reference/ado-api/schemaenum.md) valori correlati in modo specifico per i provider di dati multidimensionali. I valori sono i seguenti:  
  
-   **adSchemaCubes**  
  
-   **adSchemaDimensions**  
  
-   **adSchemaHierarchies**  
  
-   **adSchemaLevels**  
  
-   **adSchemaMeasures**  
  
-   **adSchemaMembers**  
  
 Per utilizzare valori di enumerazione di ADO con metodi o proprietà ADO MD, il progetto deve fare riferimento a librerie ADO e ADO MD. Ad esempio, è possibile utilizzare ADO **adState** valori di enumerazione con ADO MD [stato](../../../ado/reference/ado-md-api/state-property-ado-md.md) proprietà. Per ulteriori informazioni su come stabilire i riferimenti alle librerie, vedere la documentazione dello strumento di sviluppo.  
  
 Per ulteriori informazioni sui metodi e gli oggetti ADO, vedere il [riferimento all'API ADO](../../../ado/reference/ado-api/ado-api-reference.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Modello a oggetti ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO (multidimensionale) (ADO MD)](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [Panoramica di schemi e dati multidimensionali](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)   
 [Programmazione con ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Utilizzo dei dati multidimensionali](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)


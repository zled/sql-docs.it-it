---
title: Creare, modificare o eliminare indici XML selettivi secondari | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45128105-833b-40a9-9cc9-1ae03ac0b52b
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6236f26bea1a5eb579c103a4727eb0257da360c4
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2018
---
# <a name="create-alter-and-drop-secondary-selective-xml-indexes"></a>Creare, modificare o eliminare indici XML selettivi secondari
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
Viene descritto come creare un nuovo indice XML selettivo secondario oppure modificarne o eliminarne uno esistente.  
  
##  <a name="create"></a> Creazione di un indice XML selettivo secondario  
  
### <a name="how-to-create-a-secondary-selective-xml-index"></a>Procedura: Creare un indice XML selettivo secondario  
 **Creare un indice XML selettivo secondario tramite Transact-SQL**  
 Creare un indice XML selettivo secondario chiamando l'istruzione CREATE XML INDEX. Per altre informazioni, vedere [CREATE XML INDEX &#40;indici XML selettivi&#41;](../../t-sql/statements/create-xml-index-selective-xml-indexes.md).  
  
 **Esempio**  
  
 Nell'esempio seguente viene creato un indice XML selettivo secondario nel percorso `'pathabc'`. Il percorso dell'indice viene identificato dal nome fornito al momento della creazione con l'istruzione CREATE SELECTIVE XML INDEX. Per altre informazioni, vedere [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-selective-xml-index-transact-sql.md).  
  
```sql  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
  
##  <a name="alter"></a> Modifica di un indice XML selettivo secondario  
 L'istruzione ALTER non è supportata per gli indici XML selettivi secondari. Per modificare un indice XML selettivo secondario, eliminare l'indice esistente e ricrearlo.  
  
### <a name="how-to-alter-a-secondary-selective-xml-index"></a>Procedura: Modificare un indice XML selettivo secondario  
 **Modificare un indice XML selettivo secondario tramite Transact-SQL**  
 1.  Eliminare l'indice XML selettivo secondario esistente chiamando l'istruzione DROP INDEX. Per altre informazioni, vedere [DROP INDEX &#40;indici XML selettivi&#41;](../../t-sql/statements/drop-index-selective-xml-indexes.md).  
  
2.  Ricreare l'indice con le opzioni desiderate chiamando l'istruzione CREATE XML INDEX. Per altre informazioni, vedere [CREATE XML INDEX &#40;indici XML selettivi&#41;](../../t-sql/statements/create-xml-index-selective-xml-indexes.md).  
  
 **Esempio**  
  
 Nell'esempio seguente viene modificato un indice XML selettivo secondario eliminandolo e ricreandolo.  
  
```sql  
DROP INDEX filt_sxi_index_c  
  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
  
##  <a name="drop"></a> Eliminazione di un indice XML selettivo secondario  
  
### <a name="how-to-drop-a-secondary-selective-xml-index"></a>Procedura: Eliminare un indice XML selettivo secondario  
 **Eliminare un indice XML selettivo secondario tramite Transact-SQL**  
 Eliminare un indice XML selettivo secondario chiamando l'istruzione DROP INDEX. Per altre informazioni, vedere [DROP INDEX &#40;indici XML selettivi&#41;](../../t-sql/statements/drop-index-selective-xml-indexes.md).  
  
 **Esempio**  
  
 Nell'esempio seguente viene illustrata un'istruzione DROP INDEX.  
  
```sql  
DROP INDEX ssxi_index  
ON tbl  
```  
  
  
## <a name="see-also"></a>Vedere anche  
 [Indici XML selettivi &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)  
  
  

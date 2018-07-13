---
title: Opzioni (Editor di testo - XML - pagina formattazione) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 97373178-d288-4127-af37-d9f5fe1b8607
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 667b01cbdaa1e5107dcbac8a68879a94d6efc06e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37209591"
---
# <a name="options-text-editor---xml---formatting-page"></a>Opzioni (Editor di testo - XML - pagina Formattazione)
  Questa finestra di dialogo consente di specificare le impostazioni di formattazione per l'editor XML. È possibile accedere alla finestra di dialogo **Opzioni** dal menu **Strumenti**.  
  
> [!NOTE]  
>  Queste impostazioni sono disponibili quando si selezionano la cartella **Editor di testo**, la cartella **XML** e quindi l'opzione **Formattazione** nella finestra di dialogo **Opzioni**.  
  
## <a name="attributes"></a>Attributi  
 **Mantieni la formattazione manuale degli attributi**  
 Consente di non riformattare gli attributi. Impostazione predefinita.  
  
> [!NOTE]  
>  Se gli attributi sono disposti su più righe, a ogni riga di attributi verrà applicato un rientro corrispondente al rientro dell'elemento padre.  
  
 **Allinea ogni attributo su una riga separata**  
 Il secondo attributo e i successivi vengono allineati verticalmente in modo da corrispondere al rientro del primo attributo. Il testo XML seguente rappresenta un esempio del modo in cui gli attributi vengono allineati.  
  
```  
<item id = "123-A"  
      name = "hammer"  
      price = "9.95"  
</item>  
```  
  
## <a name="auto-reformat"></a>Riformatta automaticamente  
 **Quando si incolla dagli Appunti.**  
 Consente di riformattare il testo XML incollato dagli Appunti.  
  
 **Al completamento del tag di fine**  
 Consente di riformattare l'elemento al completamento del tag di fine.  
  
## <a name="mixed-content"></a>Contenuto misto  
 **Formatta contenuto misto per impostazione predefinita.**  
 Viene riformattato il contenuto misto, tranne quando il contenuto si trova in un ambito `xml:space="preserve"`. Impostazione predefinita.  
  
 Se un elemento contiene testo e markup, il contenuto viene considerato misto. Di seguito viene riportato un esempio di elemento con contenuto misto.  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
```  
  
 \</dir >  
  
## <a name="see-also"></a>Vedere anche  
 [Editor XML &#40;SQL Server Management Studio&#41;](../ssms/sql-server-management-studio-ssms.md)  
  
  

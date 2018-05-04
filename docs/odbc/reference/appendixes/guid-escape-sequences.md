---
title: Sequenze di Escape GUID | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC escape sequences [ODBC], GUID
- escape sequences [ODBC], guid
- guid escape sequence [ODBC]
ms.assetid: 71d43ef9-4a31-493e-b9e0-f864e9ef3ce6
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5edd631171acf78fd4c0ada857f72e4e50fd5ebe
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="guid-escape-sequences"></a>Sequenze di Escape GUID
ODBC utilizza le sequenze di escape per i valori letterali GUID. La sintassi di questa sequenza di escape è come segue:  
  
```  
{guid 'nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn'}  
```  
  
## <a name="remarks"></a>Osservazioni  
 Nella notazione BNF, la sintassi è:  
  
 *ODBC-guid-escape* :: =  
     *Guid ODBC-esc-iniziatore* '*valore guid*' *ODBC-esc-carattere di terminazione*  
  
 *ODBC-esc-iniziatore* :: = {  
  
 *ODBC-esc-carattere di terminazione* :: =}  
  
 *valore GUID* :: = *nodo-valore del separatore di guid-low-valore dell'orologio del separatore guid-intermedio-valore dell'orologio del clock alto valore guid-separatore separatore guid-seq-valore dell'orologio*  
  
 *separatore di GUID* :: = -  
  
 *low-valore dell'orologio* :: = *hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit*  
  
 *valore dell'intermedio orologio* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *orologio di alto valore* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *valore dell'orologio-seq* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *valore di nodo clock* :: = *hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit*  
  
 *hex_digit* :: = 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; A &#124; B &#124; C &#124; 1!d &#124; E &#124; F  
  
 La sequenza di escape letterale GUID è supportata se il tipo di dati GUID è supportato dall'origine dati. Un'applicazione deve chiamare **SQLGetTypeInfo** per determinare se questo tipo di dati è supportato.

---
title: 不支持 XML 实体引用
ms.date: 07/20/2015
f1_keywords:
- vbc31180
- bc31180
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
ms.openlocfilehash: dd86600f29fbc7c16c74085d63bfb52a4a5f76f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595821"
---
# <a name="xml-entity-references-are-not-supported"></a>不支持 XML 实体引用
实体引用 (例如， `©`) 未定义在 XML 1.0 规范是包含作为 XML 文本的值。 仅`&`， `"`， `<`， `>`，和`'`XML 文本中支持 XML 实体引用。  
  
 **错误 ID:** BC31180  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   删除不受支持的实体引用。  
  
## <a name="see-also"></a>请参阅  
 [XML 文本和 XML 1.0 规范](../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)  
 [XML 文本](../../../visual-basic/language-reference/xml-literals/index.md)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)

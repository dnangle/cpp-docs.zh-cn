---
title: '&lt;map&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
ms.openlocfilehash: 8cc4a82e08963902f9ba5c21ace759c47bdd0014
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228214"
---
# <a name="ltmapgt-functions"></a>&lt;map&gt; 函数

## <a name="swap-map"></a><a name="swap_multimap"></a>swap （map）

交换两个映射的元素。

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    map<Key, Traits, Compare, Alloctor>& left,
    map<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>参数

*然后*\
提供要交换的元素的映射，或其元素要与*左侧*地图的元素进行交换的映射。

*左中*\
其元素将与地图*权限*的元素进行交换的映射。

### <a name="remarks"></a>备注

模板函数是一个专用于容器类映射的算法，用于执行成员函数 `left` 。[swap](../standard-library/map-class.md#swap)（ `right` ）。 这是由编译器进行的函数模板偏序实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 算法类中的模板函数的常规版本 " **`template`** \< **class T**> **void 交换**（ **t&**， **t&**）" 按赋值方式工作，并且是慢速操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。

### <a name="example"></a>示例

有关使用 `swap` 的模板版本的示例，请参阅成员函数 [map::swap](../standard-library/map-class.md#swap) 的代码示例。

## <a name="swap-multimap"></a><a name="swap"></a>swap （多重映射）

交换两个多重映射的元素。

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,
    multimap<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>参数

*然后*\
提供要交换的元素的多重映射，或其元素将要与多重映射*左侧*的元素进行交换的多重映射。

*左中*\
其元素要与多重映射*权限*的元素进行交换的多重映射。

### <a name="remarks"></a>备注

此模板函数是一个专用于容器类映射的算法，该算法用于在 container 类多重映射上执行成员函数 `left` 。[swap](../standard-library/multimap-class.md#swap) （ `right` ）。 这是由编译器进行的函数模板偏序实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 算法类中的模板函数的常规版本 " **`template`** \< **class T**> **void 交换**（ **t&**， **t&**）" 按赋值方式工作，并且是慢速操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。

### <a name="example"></a>示例

有关使用 `swap` 的模板版本的示例，请参阅成员函数 [multimap::swap](../standard-library/multimap-class.md#swap) 的代码示例。

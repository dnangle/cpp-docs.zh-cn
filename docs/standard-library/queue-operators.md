---
title: '&lt;queue&gt; 运算符'
ms.date: 11/04/2016
f1_keywords:
- queue/std::operator!=
- queue/std::operator&gt;
- queue/std::operator&gt;=
- queue/std::operator&lt;
- queue/std::operator&lt;=
- queue/std::operator==
ms.assetid: 7c435b48-175c-45b0-88eb-24561044019c
helpviewer_keywords:
- std::operator!= (queue)
- std::operator&gt; (queue)
- std::operator&gt;= (queue)
- std::operator&lt; (queue)
- std::operator&lt;= (queue)
- std::operator== (queue)
ms.openlocfilehash: 8c02e79e6a300f23ac31ea876c9d4576cfe5e9a8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232919"
---
# <a name="ltqueuegt-operators"></a>&lt;queue&gt; 运算符

## <a name="operator"></a><a name="op_neq"></a>operator！ =

测试运算符左侧和右侧的 queue 对象是否不相等。

```cpp
bool operator!=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>参数

*左中*\
一个 `queue` 类型的对象。

*然后*\
一个 `queue` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果队列不相等，则为;**`false`** 如果队列相等，则为。

### <a name="remarks"></a>备注

队列对象之间的比较基于其元素的成对比较。 如果两个队列具有的元素数目相等且对应元素具有相同的值，则两个队列相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// queue_op_ne.cpp
// compile with: /EHsc
#include <queue>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queues with list base containers
   queue <int, list<int> > q1, q2, q3;

   // The following line would have caused an error because vector
   // does not support pop_front( ) and so cannot be adapted
   // by queue as a base container
   // queue <int, vector<int> > q1, q2, q3;

   q1.push( 1 );
   q2.push( 1 );
   q2.push( 2 );
   q3.push( 1 );

   if ( q1 != q2 )
      cout << "The queues q1 and q2 are not equal." << endl;
   else
      cout << "The queues q1 and q2 are equal." << endl;

   if ( q1 != q3 )
      cout << "The queues q1 and q3 are not equal." << endl;
   else
      cout << "The queues q1 and q3 are equal." << endl;
}
```

```Output
The queues q1 and q2 are not equal.
The queues q1 and q3 are equal.
```

## <a name="operatorlt"></a><a name="op_lt"></a>操作员&lt;

测试运算符左侧的 queue 对象是否小于右侧的 queue 对象。

```cpp
bool operator<(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>参数

*左中*\
一个 `queue` 类型的对象。

*然后*\
一个 `queue` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的队列小于且不等于运算符右侧的队列，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

队列对象之间的比较基于其元素的成对比较。 两个队列对象之间的小于关系基于首对不相等元素之间的比较。

### <a name="example"></a>示例

```cpp
// queue_op_lt.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queues with default deque base container
   queue <int> q1, q2, q3;

   q1.push( 1 );
   q1.push( 2 );
   q2.push( 5 );
   q2.push( 10 );
   q3.push( 1 );
   q3.push( 2 );

   if ( q1 < q2 )
      cout << "The queue q1 is less than the queue q2." << endl;
   else
      cout << "The queue q1 is not less than the queue q2." << endl;

   if ( q1 < q3 )
      cout << "The queue q1 is less than the queue q3." << endl;
   else
      cout << "The queue q1 is not less than the queue q3." << endl;
}
```

```Output
The queue q1 is less than the queue q2.
The queue q1 is not less than the queue q3.
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a>操作员&lt;=

测试运算符左侧的 queue 对象是否小于或等于右侧的 queue 对象。

```cpp
bool operator<=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>参数

*左中*\
一个 `queue` 类型的对象。

*然后*\
一个 `queue` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的队列严格小于运算符右侧的队列，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

队列对象之间的比较基于其元素的成对比较。 两个队列对象之间的小于或等于关系基于首对不相等元素的比较。

### <a name="example"></a>示例

```cpp
// queue_op_le.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2, q3;

   q1.push( 5 );
   q1.push( 10 );
   q2.push( 1 );
   q2.push( 2 );
   q3.push( 5 );
   q3.push( 10 );

   if ( q1 <= q2 )
      cout << "The queue q1 is less than or equal to "
           << "the queue q2." << endl;
   else
      cout << "The queue q1 is greater than "
           << "the queue q2." << endl;

   if ( q1 <= q3 )
      cout << "The queue q1 is less than or equal to "
           << "the queue q3." << endl;
   else
      cout << "The queue q1 is greater than "
           << "the queue q3." << endl;
}
```

```Output
The queue q1 is greater than the queue q2.
The queue q1 is less than or equal to the queue q3.
```

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

测试运算符左侧和右侧的队列对象是否相等。

```cpp
bool operator==(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>参数

*左中*\
一个 `queue` 类型的对象。

*然后*\
一个 `queue` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果队列不相等，则为;**`false`** 如果队列相等，则为。

### <a name="remarks"></a>备注

队列对象之间的比较基于其元素的成对比较。 如果两个队列具有的元素数目相等且对应元素具有相同的值，则两个队列相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// queue_op_eq.cpp
// compile with: /EHsc
#include <queue>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queues with list base containers
   queue <int, list<int> > q1, q2, q3;

   // The following line would have caused an error because vector
   // does not support pop_front( ) and so cannot be adapted
   // by queue as a base container
   // queue <int, vector<int> > q1, q2, q3;

   q1.push( 1 );
   q2.push( 2 );
   q3.push( 1 );

   if ( q1 != q2 )
      cout << "The queues q1 and q2 are not equal." << endl;
   else
      cout << "The queues q1 and q2 are equal." << endl;

   if ( q1 != q3 )
      cout << "The queues q1 and q3 are not equal." << endl;
   else
      cout << "The queues q1 and q3 are equal." << endl;
}
```

```Output
The queues q1 and q2 are not equal.
The queues q1 and q3 are equal.
```

## <a name="operatorgt"></a><a name="op_gt"></a>操作员&gt;

测试运算符左侧的 queue 对象是否大于右侧的 queue 对象。

```cpp
bool operator>(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>参数

*左中*\
一个 `queue` 类型的对象。

*然后*\
一个 `queue` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的队列严格小于运算符右侧的队列，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

队列对象之间的比较基于其元素的成对比较。 两个队列对象之间的大于关系基于首对不相等元素之间的比较。

### <a name="example"></a>示例

```cpp
// queue_op_gt.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2, q3;

   q1.push( 1 );
   q1.push( 2 );
   q1.push( 3 );
   q2.push( 5 );
   q2.push( 10 );
   q3.push( 1 );
   q3.push( 2 );

   if ( q1 > q2 )
      cout << "The queue q1 is greater than "
           << "the queue q2." << endl;
   else
      cout << "The queue q1 is not greater than "
           << "the queue q2." << endl;

   if ( q1> q3 )
      cout << "The queue q1 is greater than "
           << "the queue q3." << endl;
   else
      cout << "The queue q1 is not greater than "
           << "the queue q3." << endl;
}
```

```Output
The queue q1 is not greater than the queue q2.
The queue q1 is greater than the queue q3.
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a>操作员&gt;=

测试运算符左侧的 queue 对象是否大于或等于右侧的 queue 对象。

```cpp
bool operator>=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>参数

*左中*\
一个 `queue` 类型的对象。

*然后*\
一个 `queue` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的队列严格小于运算符右侧的队列，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

队列对象之间的比较基于其元素的成对比较。 如果两个队列具有的元素数目相等且对应元素具有相同的值，则两个队列相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// queue_op_ge.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2, q3;

   q1.push( 1 );
   q1.push( 2 );
   q2.push( 5 );
   q2.push( 10 );
   q3.push( 1 );
   q3.push( 2 );

   if ( q1 >= q2 )
      cout << "The queue q1 is greater than or equal to "
           << "the queue q2." << endl;
   else
      cout << "The queue q1 is less than "
           << "the queue q2." << endl;

   if ( q1>= q3 )
      cout << "The queue q1 is greater than or equal to "
           << "the queue q3." << endl;
   else
      cout << "The queue q1 is less than "
           << "the queue q3." << endl;
}
```

```Output
The queue q1 is less than the queue q2.
The queue q1 is greater than or equal to the queue q3.
```
